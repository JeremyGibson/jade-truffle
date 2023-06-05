SAT Django Project
==================================

SAT Django Project is a
[cookiecutter](https://github.com/cookiecutter/cookiecutter) template
designed to generate a greenfield Django project.


Requirements
------------

-   Python >= 3.8 < 3.10 # Until the backports bug is fixed in 3.11
-   pip-tools
-   cookiecutter
-   A virtual environment manager
-   direnv
-   pyenv
-   nvm

Installation
------------

Create a Python virtual environment with your tool of choice. For
purposes of these instructions we'll call the environment
`sat-app`.

Enable your environment and install cookiecutter:

    (sat-app)$ pip install cookiecutter

Now you have an environment that can install cookiecutter templates.

Next use cookiecutter to build a project using `sat-app`:

    (sat-app)$ cookiecutter https://github.ncsu.edu/SAT/django-template

Options
-------

The cookiecutter will run through a series of configuration options

1. Project Name: This can be anything you like (e.g. Apple Pie)

1. Project Slug: Generated from the Project Name, but can be overridden.
   Used in most configuration options in the generated project.
    
        apple_pie/apple_pie/settings
        apple_pie/apple_pie/urls.py

1. Project Type: `django`
1. Testing Type: `django` or `pytest`
1. CSS Style: `sass` or `tailwind`
1. CI/CD: `actions`   
1. Cloud Provider: `gcp`
1. Local Postgres Port: Defaults to `5432`
   This is used for local dev so you can set this to any port you like. 
   
        NOTE: If you have a postgres server running locally on port 5432, you
        will want to choose a different port than 5432.

1. Primary App: Will be used as the main app in the projects apps directory.
   
        For example: `apple_pie/apps/apple_pie`

1. Project Domain Name:
    
        Defaults to `test.ehps.ncsu.edu`

The generated project has a README that details the steps for install.
