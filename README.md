Plum: Prompted Language Model Applications
==========================================

Plum is a framework for LLM-based web applications for education (i.e., with a
focus on instructors and their classes of students as users).

This repository also contains two applications that are built on Plum:

1. CodeHelp: A tool for assisting students in computer science classes without
   giving them solution code. <https://codehelp.app/>
2. Starburst: A topic-exploration tool for writing assignments.
   <https://strbrst.xyz/>


Install
-------

1. Create and activate a Python virtual environment.
   Requires Python 3.9 or higher.

2. Install the plum package and apps in 'editable' mode

  pip install -e .


Set Up an Application
---------------------

1. In the root of the repository, create an instance folder for the database:

  mkdir instance

2. In the root of the repository, create .env and populate it:

  FLASK_INSTANCE_PATH=instance
  SECRET_KEY=[a secure random string -- used to sign session cookies]
  OPENAI_API_KEY=[your OpenAI API key]

Optionally, set any of the following pairs with IDs/secrets obtained from
registering your application with the given authentication provider:

  GOOGLE_CLIENT_ID=[...]
  GOOGLE_CLIENT_SECRET=[...]
  GITHUB_CLIENT_ID=[...]
  GITHUB_CLIENT_SECRET=[...]
  MICROSOFT_CLIENT_ID=[...]
  MICROSOFT_CLIENT_SECRET=[...]

Then, to set up the CodeHelp app, for example:

3. Initialize database

  flask --app codehelp initdb

4. Create at least one admin user

  flask --app codehelp newuser --admin [username]

This will create and display a randomly-generated password.
To change the password:

  flask --app codehelp setpassword [username]


Running an Application
----------------------

For example, to run the CodeHelp app:

  flask --app codehelp run
  
  # or, during development:
  flask --app codehelp --debug run


Running Tests
-------------

First, install test dependencies:

  pip install -e .[test]

Run all tests:

  pytest

For code coverage report:

  pytest --cov=src/plum --cov=src/codehelp --cov-report=html && xdg-open htmlcov/index.html

For mypy type checking:

  mypy


Author
------

Plum and the included applications are by Mark Liffiton.


Licenses
--------

Plum and the included applications are licensed under the GNU Affero General
Public License version 3 (AGPL-3.0-only).

Brand icons from [Simple Icons](https://simpleicons.org/) are licensed under
CC0-1.0.  Other icons from [Lucide](https://lucide.dev/) are licensed under the
Lucide ISC license.

For the text of these licenses, see the LICENSES directory.