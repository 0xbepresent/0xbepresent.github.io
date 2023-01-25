---
title: Mocking functions in all Django Test Enviroment
date: 2015-02-02
---

Sometimes, when you're doing tests for your application you have to be careful
with the code that you're testing.

For example, we have a function that is making a request to the Twitter Server and if we do a test for that function, probably we'll be doing real requests to the Twitter Servers. So, in this case, we have to be careful because, strictly, we don't have to make real requests in our tests.

In the default case, when you run ./manage.py test, <a href="https://docs.djangoproject.com/en/1.7/topics/testing/advanced/#using-the-django-test-runner-to-test-reusable-applications">Django looks at the TEST RUNNER setting</a> to determine what to do. By default, TEST RUNNER points to <a href="https://docs.djangoproject.com/en/1.7/_modules/django/test/runner/">'django.test.runner.DiscoverRunner'</a>. This class defines the default testing behavior. So, you can use any test framework that can be executed from Python code.

The interesting thing is that you can modify the test execution process. I mean, you can do 'something' before, during or after the test suite execution.

<a href="https://gist.github.com/misalabs/3ff42213dffcf0981e83">This is an example</a> which show you how to override the Django DiscoverRunner Class and put your own TestRunner, but the trick is that you can do something before and after the execution. In this case, I mock the get requests then return
None value. So, if you're testing a function which is doing requests to the Twitter Server, the function won't be doing real requests to the Twitter Server.

The point is that you're able to mock functions before the execution tests, of course, that depends of the circunstances because not everything should be mocked.
