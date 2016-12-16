Glossary
========

.. glossary::

  Aggregate
    Applying a function to a Measure, such as summing, calculating the mean etc

  Backdrop
    An application that is part of the performance platform. It provides the `read and write API <https://github.com/alphagov/backdrop>`_ for data.

  Chart
    A graphical representation of a Measure and a Dimension (eg number of applications by channel)

  Dashboard
    A page showing multiple metrics, typically for a single :term:`service`

  Dataset
    A collection of data of a particular type. In relational terms, this is a table.
    In non-relational terms, this is a collection of documents.

  Data type
    Each :term:`Dataset` stores a particular type of data, eg current traffic volume

  Dimension
    A non-numeric type of :term: `Field` eg an operating system or browser

  Element
    A component of a Visualisation such as a chart or aggregate summary

  Field
    A 'column' in a dataset

  Measure
    A numeric type of :term: `Field`, eg number of applications. A Measure may be aggregated

  Metric
    A specific data series, eg completion rate, user satisfaction, page load time, uptime etc

  Module
    A module is a :term:`metric` and a :term:`visualisation` together, eg digital take-up shown as a line chart

  Observation
    A 'row' in a dataset

  Service
    A transactional service is a facility that enables users to transact with government, eg Renew you car tax, Apply for Carer's Allowance, Apply for a fishing rod licence etc.

  Service Group
    A group of closely related services, eg Carer's Allowance service group includes applications, existing claims, appeals etc

  Spotlight
    An application that is part of the performance platform. It is responsible for `rendering data <https://github.com/alphagov/backdrop>`_ from the :term:`Backdrop` API to display visualisations of service performance

  Stageprompt
    A JavaScript library that provides an adapter over analytics software

  Transaction
    An exchange of information, money, permissions, goods etc that takes place between government and users (individuals, businesses and other organisations). Examples include an application for a passport, a renewal of a patent, an update to the Organ Donation Register.

  Visualisation
    A set of Elements using the Measures and Dimensions from the Dataset
