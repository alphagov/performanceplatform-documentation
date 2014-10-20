Write API
=========

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

- should use a URL like `https:/{write-host}/<data-set-name>`, where
  `write-host` could be something like `www.performance.service.gov.uk`
- must have an HTTP Content-Type header of application/json
- must have a valid `Authorization header <https://tools.ietf.org/html/rfc6750#section-2.1>`_


The `backdropsend <https://github.com/alphagov/backdropsend backdrop-send>`_ tool provides a command line interface to the API. This adds support for retrying.

See the example below using curl (all examples using curl 7.24)::

  > curl -X POST -d '[{"name":"Jane"}, {"name":"John"}]' \
         -H 'Authorization: Bearer <your-token>' \
         -H 'Content-Type: application/json' \
         'http://{write-host}/<data-set-name>'
