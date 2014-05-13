Sending data to backdrop
========================

.. toctree::
  :maxdepth: 2

  /send-to-backdrop/index

So you have a data-set and an access token, how do you actually get your data into backdrop?

By HTTP API
-----------
Backdrop exposes a very small HTTP API for pushing data in. There is one endpoint per data-set that can accept one or more JSON records being sent to it vi a POST. You authorize each request by adding an Authorization header with the secret access token you should have been provided for each data-set.

The client request:

- should use a URL like `https://<backdrop-write-host>/<data-set-name>`, where `backdrop-write-host` is eg `www.preview.performance.service.gov.uk`
- must have a content type of application/json
- must have a valid Authorization header

The :doc:`/send-to-backdrop/index` tool provides a command line interface to the API.

See the example below using curl (all examples using curl 7.24)::

  curl -X POST -d '{"name":"Jane"}' -H 'Authorization: Bearer <your-token>' -H 'Content-type: application/json' 'http://<backdrop-write-host>/<data-set-name>'

Often you'll need to send multiple records to backdrop at once. You can do this by sending an array of records::

  curl -X POST -d '[{"name":"Jane"},{"name":"John"}]' -H 'Authorization: Bearer <your-token>' -H 'Content-type: application/json' 'http://<backdrop-write-host>/<data-set-name>'

.. warning:: When reading back data you've pushed to the platform, beware of server-side caching. It's advisable to develop against a local instance of the platform with no caching to ensure the data you're seeing is up-to-date.

By uploading a file
-------------------

Backdrop also accepts file uploads through its admin interface. Log on with your signon account and you will be presented with a list of data-sets you can upload to. Upload files should be in CSV or Excel (depending what has been configured for your data-set). The first row must contain the field names and each subsequent line is values for a single record. The same rules around field names and special fields apply as for the JSON API (see below).

What is a record?
-----------------

A record is a flat (not nested) JSON object with zero or more attributes that can be saved into backdrop and aggregated on at a later stage. In order to be a valid record it must comply to some rules.

Valid field names
~~~~~~~~~~~~~~~~~

All record field names:

- must start with a letter
- must be alphanumeric
- may contain underscores
- some special field names start with an underscore

.. note::

  {"name": "Jane", "home_town": "Godalming"}

.. warning::

  {"name": "Jane", "home town": "Godalming"} # Spaces are not allowed

  {"_name": "Jane", "home_town": "Godalming"} # Underscore prefix is reserved

  {"1_name": "Jane", "2_home_town": "Godalming"} # First character must be a letter


Special fields
~~~~~~~~~~~~~~

Backdrop understands some special field names that it will treat in specific ways.

The `_id` field
+++++++++++++++

The `_id` field is a unique identifier (or primary key) for the record. You can use this if you are going to want to update records or prevent defaults. When sending a record to backdrop if a record with the provided `_id` already exists in the data-set it will be overwriten.

The `_id` field:

- must be a string
- must not contain spaces
- must not be empty

The `_timestamp` field
++++++++++++++++++++++

The `_timestamp` field is the central field when working with time series data. It represents the time stamp of a record. It allows you to query by time ranges and aggregate by predefined time periods (ie. week, month).

The `_timestamp` field:

- must be a string
- must be of the form (`2013-12-31T00:00:00+00:00`)

.. note::

  Atom says some nice stuff about date formats -- we should take a look at that.
