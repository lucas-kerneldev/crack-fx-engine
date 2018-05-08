Testing
=======

Testing is a very important part of the development process. It allows us to
verify the functionality of our projects as well as judge the quality of our
work.

At Mozilla, we have multiple ways of testing our code, including:

- Unit tests and integration tests, which are automated tests that verify that
  pieces of code work as expected.
- End-to-end tests, automated tests which check the functionality of a project
  as a whole. For example, simulating clicks in a web browser to test how a
  site functions.
- Manual testing, which is performed by a human and involves verifying features
  work as expected and exploratory tests.

Assessing and managing risk
---------------------------

The end goal of testing is to manage the risk of something going wrong with
your project. To this end, one of the first steps you should take is to assess
the risk of each area of your project.

More concretely, some parts of your project are going to be more likely to fail
than others. Also, some parts of your project are more important than others,
and it may be more harmful for them to fail than less important parts.

A risk assessment lists out the different parts of your project (such as
certain webpages or parts of an API) and ranks them based on their importance.
For example, a news site rank being able to read existing articles as more
important than being able to submit new articles. Ranking these parts allows
you to make decisions about which to test more and what kind of tests to run.

Some projects rely on `Travis CI`_ for executing their tests.

For Django projects, these tests live within the ``tests`` module of each
included Django application. For Node-based projects, they normally live in
a directory named ``test`` or ``tests`` at the root of the repository. Refer to
your project's documentation for more details.

End-to-end tests
----------------

End-to-end tests simulates how your project will be used by users and verifies
that it behaves as expected. This is most commonly applied to websites, where
we use tools like Selenium_ to simulate users interacting with the website.

For many sites, these tests are written by WebQA contributors and run against
the various :doc:`server environments <servers>`.

.. _Selenium: http://www.seleniumhq.org/projects/webdriver/

Manual testing
--------------

Manual testing is good old-fashioned human-powered testing, where a living,
breathing human uses your project and checks for any errors. Typically this is
either for verifying that a new feature works as expected, or for free-form
exploratory testing.

In addition to writing automated tests, you almost certainly should be manually
testing any changes you make to a project.

Testing tools
-------------

The following is a non-exhaustive, possibly-out-of-date list of tools and
libraries that may aid you in testing your projects.

General
^^^^^^^

- Jenkins_ is a continuous integration server that builds and/or tests software
  projects continuously.
- `Travis CI`_ is a hosted continuous integration service that integrates with
  Github.
- Selenium_ is a tool for automating browsers, often for testing purposes.

.. _Jenkins: https://jenkins.io/
.. _Travis CI: https://travis-ci.org/

Python
^^^^^^

- pytest_ is a highly recommended testing library for Python, with a great
  plugin ecosystem. Some common plugins we're using include

   - `pytest-testrail`_ for sending test run details to our `Testrail` server
   - `pytest-bugzilla-notifier`_ for sending test summaries to Bugzilla tickets

- `factory-boy`_ replaces test fixtures with factories that generate test
  objects easily. It integrates with the Django ORM to generate model instances
  with a very conveninent syntax.

- Mock_ is one of the most popular libraries for replacing parts of the system
  you're testing with mock objects and asserting things about their behavior.

.. _factory-boy: https://factoryboy.readthedocs.io/
.. _Mock: http://www.voidspace.org.uk/python/mock/
.. _pytest: http://pytest.org
.. _pytest-testrail: https://pypi.python.org/pypi/pytest-testrail
.. _pytest-bugzilla-notifier: https://pypi.python.org/pypi/pytest-bugzilla-notifier/0.1.2

Node / JavaScript
^^^^^^^^^^^^^^^^^

- Mocha_ is a framework for running tests on node.js and in the browser.
- Chai_ is an assertion library with many interfaces to accomodate different
  testing styles.
- Karma_ allows you to execute JavaScript code in multiple real browsers.

.. _Mocha: http://visionmedia.github.io/mocha/
.. _Chai: http://chaijs.com/
.. _Karma: http://karma-runner.github.io
