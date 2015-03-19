Write API
#########

We expose a simple HTTP API for storing data in the Performance
Platform.

There is one endpoint per data-set that can accept one or more JSON
records being sent to it via a POST. We use
`OAuth 2.0 Bearer tokens <https://tools.ietf.org/html/rfc6750#section-2.1>`_
to authenticate attempts to write to a data set.

You authorize each request by adding an Authorization
header with the secret access token you should have been provided for
each data-set.

The client request:

- should use a URL like `https://<write-host>/data/<data-group>/<data-type>`, where
  `<write-host>` could be something like `www.performance.service.gov.uk`
- must have an HTTP Content-Type header of application/json
- must have a valid `Authorization header <https://tools.ietf.org/html/rfc6750#section-2.1>`_


The `backdropsend <https://github.com/alphagov/backdropsend>`_ tool provides a command line interface to the API. This adds support for retrying.

Adding data
===========

.. http:post:: /data/(string:data_group)/(string:data_type)

  :synopsis: Insert data into a data set by sending a POST request with JSON in the body.

  **Example request**:

  .. sourcecode:: http

    POST /data/carers-allowance/transaction-count HTTP/1.1
    Host: www.performance.service.gov.uk
    Authorization: Bearer abcdefghijklmnopqrstuvwxyz0123456789abcdefghijklmnopqrstuvwxyz01
    Content-Type: application/json

    [
      {
        "_id": "unique-identifier-1",
        "_timestamp": "2015-01-01T00:00:00Z",
        "count": 123
      },
      {
        "_id": "unique-identifier-2",
        "_timestamp": "2015-01-02T00:00:00Z",
        "count": 456
      }
    ]

  All of the above headers are important.

  **Example response**:

  .. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "status": "ok"
    }

  :reqheader Authorization: required OAuth token to authenticate the request
  :reqheader Content-Type: type of the request body (only JSON is currently supported)

  :<json string _timestamp: A datetime representing the start of the
    period that the data refers to. Required.
  :<json string _id: A string that uniquely identifies
    that record. If a record with that identifier already exists, it will be overwritten. Optional.

  :statuscode 200: data from the request body was stored in the data set

Emptying a data set
===================

.. http:put:: /data/(string:data_group)/(string:data_type)

  :synopsis: Empty a data set by sending an empty array as a PUT request.

  **Example request**:

  .. sourcecode:: http

    PUT /data/carers-allowance/transaction-count HTTP/1.1
    Host: www.performance.service.gov.uk
    Authorization: Bearer abcdefghijklmnopqrstuvwxyz0123456789abcdefghijklmnopqrstuvwxyz01
    Content-Type: application/json

    []

  **Example response**:

  .. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "message": "carers_allowance_transaction_count now contains 0 records",
        "status": "ok"
    }

  :reqheader Authorization: required OAuth token to authenticate the request

  :statuscode 200: data set now contains no records

Client implementations
======================

We provide several implementations of client code to talk to the Performance Platform:

- `Go <https://github.com/alphagov/performanceplatform-client.go>`_
- `Java implementation <https://github.com/alphagov/pp-db-collector-template>`_ intended to periodically poll a JDBC data store and push data Performance Platform
- `JavaScript <https://github.com/alphagov/performanceplatform-client.js>`_
- `Python <https://github.com/alphagov/performanceplatform-client.py>`_
