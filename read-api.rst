.. _read-api:

:orphan:

Read API
========

The following parameters can be specified when using the Read API:

'start_at'
  The date from which a date range starts. Used in conjunction with 'end_at'.

'end_at'
  The date from which a date range ends. Used in conjunction with 'start_at'.

'filter_by'
  A field to filter by. Must be a field name and value separated by a colon (:) eg. 'authority:Westminster'.

'period'
  The unit we want the results to be in. Must be one of 'hour', 'day', 'week', 'month' or 'quarter'.

'group_by'
  A field to group by. Must be an existing field name.

'sort_by'
  A field to sort by. Must be a field name and sort direction ('ascending' or 'descending') separated by a colon (:) eg. 'authority:ascending'.

'limit'
  A maximum amount of values to return. Must be a positive integer.

'collect'
  A field to perform an agregation operation on. Must be a field name and sort direction ('sum', 'count', 'set' or 'mean') separated by a colon (:) eg. 'size:mean'.

'date'
  When specified with 'delta' (and instead of 'start_at' and 'end_at') determines one end of a relative date range. If only 'delta' is specified the current datetime will be used.

'delta'
  When specified instead of 'start_at' and 'end_at', is added to 'date' (which will be now if unspecified) to determine the other end of a relative date range. This is measured in units of 'period' and may be negative.

