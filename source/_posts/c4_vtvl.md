---
title: C4 audit report - VTVL contest
date: 2023-02-02
---

I participated in the [VTVL contest](https://github.com/code-423n4/2022-09-vtvl) from September 20, 2022 to September 23, 2022. I will explain my first medium report as a smart contract auditor. You can read the full audit report [here](https://code4rena.com/reports/2022-09-vtvl).

The VTVL protocol allows users to generate and deploy token vesting smart contracts through their platform.

Medium severities: 1

## Max supply limit for the VariableSupplyERC20Token contract could be bypassed.
Severity: medium

The [project has an ERC20](https://github.com/code-423n4/2022-09-vtvl/blob/f68b7f3e61/contracts/token/VariableSupplyERC20Token.sol#L40) contract that allows minting at will. You can see the next code:

```javascript
/**
@notice A ERC20 token contract that allows minting at will, with limited or unlimited supply. No burning possible
@dev
@param name_ - Name of the token
@param symbol_ - Symbol of the token
@param initialSupply_ - How much to immediately mint (saves another transaction). If 0, no mint at the beginning.
@param maxSupply_ - What's the maximum supply. The contract won't allow minting over this amount. Set to 0 for no limit.
*/
constructor(string memory name_, string memory symbol_, uint256 initialSupply_, uint256 maxSupply_) ERC20(name_, symbol_) {
    // max supply == 0 means mint at will. 
    // initialSupply_ == 0 means nothing preminted
    // Therefore, we have valid scenarios if either of them is 0
    // However, if both are 0 we might have a valid scenario as well - user just wants to create a token but doesn't want to mint anything
    // Should we allow this?
    require(initialSupply_ > 0 || maxSupply_ > 0, "INVALID_AMOUNT");
    mintableSupply = maxSupply_;
    
    // Note: the check whether initial supply is less than or equal than mintableSupply will happen in mint fn.
    if(initialSupply_ > 0) {
        mint(_msgSender(), initialSupply_);
    }
}

function mint(address account, uint256 amount) public onlyAdmin {
    require(account != address(0), "INVALID_ADDRESS");
    // If we're using maxSupply, we need to make sure we respect it
    // mintableSupply = 0 means mint at will
    if(mintableSupply > 0) {
        require(amount <= mintableSupply, "INVALID_AMOUNT");
        // We need to reduce the amount only if we're using the limit, if not just leave it be
        mintableSupply -= amount;
    }
    _mint(account, amount);
}
```

If maxSupply was assigned different to 0, the mint function should limit the token creation. Comment in the code says:

```
@param maxSupply_ - What's the maximum supply. The contract won't allow minting over this amount. Set to 0 for no limit.
```

## Impact

The problem is that even when the maxSupply was assigned different to 0, the restriction was ignored in the mint function because the function will reduce the mintableSupply until 0 and zero also means "no limit".

An unlimited supply will make the token inflationary, behavior that is not correct if the creator setting up the max supply.

## Proof of concept

```python
from brownie import VariableSupplyERC20Token, accounts
import pytest


@pytest.fixture()
def deployer():
    """Deploy account."""
    return accounts[0]


@pytest.fixture()
def investor1():
    """Investor1 account."""
    return accounts[1]


def test_mintTokenMaxSupply(deployer, investor1):
    """
    Test the max supply limit.
    If mintableSupply > 0, check mint() fails with amount > mintableSupply.
    """
    vse = VariableSupplyERC20Token.deploy(
        "bepresent", "btp", 0, 1000, {"from": deployer}
    )
    # Mint 1000 tokens to the investor1
    vse.mint(investor1, 1000, {"from": deployer})
    assert vse.balanceOf(investor1) == 1000
    assert vse.mintableSupply() == 0  # The maxSupply was reached

    # Mint 10,000 more tokens for the investor1. The maxSupply was ignored
    # and Investor has more tokens than allowed
    vse.mint(investor1, 10000, {"from": deployer})
    assert vse.balanceOf(investor1) == 11000
    assert vse.mintableSupply() == 0
```

## Recommended Mitigation

Consider a standard implementation https://docs.openzeppelin.com/contracts/2.x/erc20-supply#fixed-supply