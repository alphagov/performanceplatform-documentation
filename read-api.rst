.. _read-api:

Read API
========

The following parameters can be specified when using the Read API:

'start_at'
  The date/time from which a time span starts. Must be provided in full IS8601_ format. Used in conjunction with 'end_at' or 'duration'.

'end_at'
  The date/time from which a time span ends. Must be provided in full ISO8106_ format. Used in conjunction with 'start_at' or 'duration'.

'filter_by'
  A field to filter by. Must be a field name and value separated by a colon (:) eg. 'authority:Westminster'.

'period'
  The unit of time we want the results to be in. Must be one of 'hour', 'day', 'week', 'month' or 'quarter'.

'group_by'
  A field to group by. Must be an existing field name.

'sort_by'
  A field to sort by. Must be a field name and sort direction ('ascending' or 'descending') separated by a colon (:) eg. 'authority:ascending'.

'limit'
  A maximum amount of values to return. Must be a positive integer.

'collect'
  A field to perform an agregation operation on. Must be a field name and sort direction ('sum', 'count', 'set' or 'mean') separated by a colon (:) eg. 'size:mean'.
  This is only applicable when a 'period' or 'group_by' is being used.

'duration'
  A number of periods used with 'period' and a 'start_at' or 'end_at' to define a relative time span. This is explained further in _`Defining Time Spans`.

Defining Time Spans
===================

A time span can be provided in two ways. The simplest way is to provide a 'start_at' and an 'end_at' directly. However,
a time span can also be provided with the use of the 'duration' parameter. Providing a time span as a relative time span
can only be done if a 'period' is also provided. 

start_at=2012-12-12T00:00:00
period=day
duration=10

is equivalent to

start_at=2012-12-12T00:00:00
end_at=2012-12-22T00:00:00
period=day

and

end_at=2012-12-12T00:00:00
period=day
duration=10

is equivalent to

start_at=2012-12-02T00:00:00
end_at=2012-12-12T00:00:00
period=day


TODO: Some description about the different semantics around how time series are expanded (to fit a provided time span) and shifted (when dealing with relative time spans).

.. _ISO8601: http://en.wikipedia.org/wiki/ISO_8601
