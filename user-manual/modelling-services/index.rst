.. _modelling-services:

Modelling services
##################

Across government, departments and agencies manage the running of services supporting individuals and business .....

Blurb about 'service' is an overloaded word!

Within each organisation, the facilties offered to users will have their own 'language' to describe....

In order to present a consistent and coherent view of how government services are performing in supporting the needs of their users, the 
Performance Platform needs a structured view of 'service' to allow dashboards to be presented at the right level and metrics
preesented in a way that supports comparison 

The basic model
===============

TODO remove business-speak here

Quick section on the intersect between 'purpose'(facility), process, exposure of process to users as transactions

Intro to 'org service groups' assigned to orgs/dept/agencies

Alow breakdown to suite org

Introduce 'transaction' in terms of the net effect of supporting the user reaching a goal

The service 'hierarchy' -- intro to 'type
========================================

Show our hierarchy, its flexibility and example mappings onto existing service -- choose complex/mid/simple

Understand service and data in context of implementation
========================================================

How to start mapping the data to support metrics from underlying implementations

NOTE: service implementation should absolutely aim to minimise impact of way metrics are presented -- de-couple the data source and aggregation from the metric

Links to Data group/type/set

Rules -- map the data group to the highest level of metric aggregation required
create datasets as high up the hierarchy as long as data from multiple sources can be uniquely identified within the set

examples

Considerations for presentation
-------------------------------

How is the data to be converted to metrics and for what audience

* `Organisational view of service`_ -- orgs will aggregate within the hierarchy of a specific organisational service (or group)
* `Transactional user view of service`_ -- individuals will aggregate at the level of associated transactions that provide them with their goal

The two are not exclusive -- metrics can be presented from the same underlying datasets -- service managers must be cogniscent of their options when modelling how their service performance data is to be used

.. _`Organisational view of service`: organisational-view
.. _`Transactional user view of service`: transaction-user-view

.. toctree::
  :hidden:

  organisational-view/index
  transaction-user-view/index

