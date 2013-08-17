Transactions Explorer
=====================

The `Transactions Explorer`_ (repo_) is a statically generated website in HTML
and JavaScript. The site is generated from a CSV file which is downloaded
using the Google Drive API.

.. _Transactions Explorer: https://www.gov.uk/performance/transactions-explorer
.. _repo: https://github.com/alphagov/transactions-explorer

Building the Site
~~~~~~~~~~~~~~~~~

Assuming you have the project checked out and all tests passing...

1. Ensure you have access to the "Transactions Explorer [feed]" `Google Doc`_.

.. _Google Doc: https://docs.google.com/a/digital.cabinet-office.gov.uk/spreadsheet/ccc?key=0AiLXeWvTKFmBdFpxdEdHUWJCYnVMS0lnUHJDelFVc0E#gid=44

2. Enable the Google Drive API on the `Google APIs Console`_

    1) If you aren't already using the API console click on 'create new project' when prompted
    2) Change the status of Drive API to on in the services tab
    3) On the API access tab click on 'Create an OAuth 2.0 client ID...' or 'Create another client ID...'
    4) Choose installed application
    5) Download the JSON file to the data directory

.. _Google APIs Console: https://code.google.com/apis/console

3. Run ``python fetch_csv.py``, this will download the google doc as a csv into the data folder.
   To get a newer version of the csv run this command again.

4. Run ``python create_pages.py``, this will create a directory called output and render
   the transactions explorer pages, the public consumable csv and a the search.json file
   into that folder. It will also copy across all of the javascript needed for the search
   and treemap features.

5. You can browse the site by running ``./serve.sh`` this will start a stub http server
   which will serve the pages without the .html postfix from http://localhost:8080/

Deployment
~~~~~~~~~~

Like any good GDS app, Transactions Explorer is deployed using Jenkins.

Building the tarball
--------------------

On ``deploy.preview.performance``, run the job ``transactions-explorer-build``.
This will build a preview and production tarball, and trigger a
downstream job to update preview using ``deploy.preview``.

This build job is also triggered by a successful Travis build (which results
in an updated git release tag). Preview is therefore kept up to date by
successful builds from master.

Note: the Transactions Explorer build requires a version of Python which is
unavailable on GOV.UK CI infrastructure.

Deploying to staging and production
-----------------------------------

Build the tarball that you want to want to deploy using the above job. Use
GOV.UK's ``deploy.staging`` and ``deploy.production`` and run the deploy jobs
for Transactions Explorer with the artefact ID you just built as a parameter.
