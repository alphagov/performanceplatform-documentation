.. _dashboards:

Dashboards
##########

The performance platform is built to support a flexible ..........

Dependent on the subject of a dashbaord: service transactions, service aggregates ....., 
the performance platfomr have a number of templates that reflect the type of 'thing' being
measured and the metrics that are regularly prsented for those 'things'

Types of dashboard
------------------
* `Transactional service dashboards`_ - one liner
* `KPI dashboards`_ - one liner
* `Aggregate dashboards`_ - one liner
* `Service overview dashboards`_ - one liner
* `High volume service dashboards`_ - one liner
* `Low volume service dashboards`_ - one liner

NOTE - Think there should be Service transaction group/Service/Service group dashboards for intermediaries

Choosing the dashboard type
---------------------------

The dasshboard types listed above are templates for presenting metrics.  They allow flexible combination of 
metrics modules to provide the broadest overview of how a service or transactional service are operating and 
allow users to ......

The service manager has control over which metrics to display on which dashboard .... need some notes/guidance 
on what modules of what metrics make sense

Selecting the user view
-----------------------
Some blurb re. the focus of the dashboard groupings - transactional services - it is about the user.
Aggeragtion of dashboard can be both a reflection of the transaction end-user view (IMPORTANT), but also
the view for the service manager operating within an organisation (see hierarchy of service)
Need to maybe show picture/graph of how the same metrics can be presented in different groupings dependent
on the primary audiences

Metrics mapping
---------------

The table below shows (from working with existing service managers) which metrics (and as a consequence modules)
can/should be present on which type of dashboard

**Metrics - Dashboard Map**

+----------------------------+----------------------+--------------------------------------------------------------------------+
|                            |Dashboard type                                                                                   |
+                            +----------------------+-------------------+------------+--------------------+--------------------+
|Metric                      |Transactional service |KPI                |*other-tbc* |High volume service |Low volume service  |
+============================+======================+===================+============+====================+====================+
|cost per transaction        |optional\ :sup:`1`    |optional\ :sup:`1` |            |mandatory           |                    |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|user satisfaction           |mandatory             |mandatory          |            |optional\ :sup:`2`  |                    |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|completion rate             |mandatory             |mandatory          |            |optional\ :sup:`2`  |                    |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|digital take-up             |mandatory             |mandatory          |            |optional\ :sup:`2`  |                    |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|live service usage          |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|transactions by channel     |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|completion at each stage    |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|page load time              |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|service uptime              |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|transaction volumes         |optional              |*n/a*              |            |mandatory\ :sup:`3` |mandatory\ :sup:`3` |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|site visits                 |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|device usage                |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|browser usage               |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|help usage                  |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|bespoke                     |optional              |*n/a*              |            |*n/a*               |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+
|digital transaction volumes |optional              |                   |            |optional \ :sup:`3` |*n/a*               |
+----------------------------+----------------------+-------------------+------------+--------------------+--------------------+

:sup:`1` - organisations may not be able to break down the *cost per transaction* at the transactional service level. It **MUST** per provided on an alternative dashboard at the appropriate level of aggregation.

KPI dashboards     Aggregate dashboards Service overview dashboards High volume service dashboards Low volume service dashboards

.. _`Transactional service dashboards`: transactional-service-dashboards/index.html
.. _`KPI dashboards`: kpi-dashboards/index.html
.. _`Aggregate dashboards`: aggregate-dashboards/index.html
.. _`Service overview dashboards`: service-overview-dashboards/index.html
.. _`High volume service dashboards`: high-volume-service-dashboards/index
.. _`Low volume service dashboards`: low-volume-service-dashboards/index

.. toctree::
  :hidden:
  
  transactional-service-dashboards/index
  kpi-dashboards/index
  aggregate-dashboards/index
  service-overview-dashboards/index
  high-volume-service-dashboards/index
  low-volume-service-dashboards/index