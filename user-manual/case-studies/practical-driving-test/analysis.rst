Analysis
********

The analysis phase of work focuses on how the needs of the Service Manager can be translated into one or more dashboards based on:

* Metrics identified as having value and how they can be presented
* Identified and agreed data sources
* Ability to integrate data sources with the performance platform
* Additional metrics that can be derived 

With the options available, this phase is then evaluated in terms of cost/benefit for the Service Manager and a decision to what/if to proceed with.

Business analysis
=================

With an understanding of how the service(s) operated and how the underpinning IT systems supported the service, a more detailed analysis of what metrics would be both valuable and achievable for the service manager. This activity brought together the service manager need, the mandatory KPI’s and a set of metrics the performance platform team had identified from previous engagements that could also be derived given the data sources available.

A number of metrics could be derived directly from the data sources identified without ‘intrusive changes’ to existing applications. Other metrics would require changes to the deployed applications. Evaluation of the impact and associated cost was considered in this phase.

*NOTE: The following table is the result of a number of iterations of metrics requirements and data availability from the technical analysis (see later section)*

+-----------------------+----------------------------------------+
|                       |Dashboard                               |
+-----------------------+----------+-------------+---------------+
|Metric                 |Overview  |Book service |Change service |
+-----------------------+----------+-------------+---------------+
|Live service usage     |Yes       |No\ :sup:`1` |No\ :sup:`1`   |
+-----------------------+----------+-------------+---------------+
|Breakdown by service   |Yes       |No           |No             |
+-----------------------+----------+-------------+---------------+
|User device type       |Yes       |No\ :sup:`1` |No\ :sup:`1`   |
+-----------------------+----------+-------------+---------------+
|Service availability   |Yes       |Yes\ :sup:`2`|Yes\ :sup:`2`  |
+-----------------------+----------+-------------+---------------+
|Transactions by channel|No        |Yes          |Yes            |
+-----------------------+----------+-------------+---------------+
|User satisfaction      |No        |Yes          |Yes            |
+-----------------------+----------+-------------+---------------+
|Digital take-up        |No        |Yes          |Yes            |
+-----------------------+----------+-------------+---------------+
|Completion rate        |No        |Yes          |Yes            |
+-----------------------+----------+-------------+---------------+
|Users at each stage    |No        |Yes          |Yes            |
+-----------------------+----------+-------------+---------------+
|Help usage             |No        |Yes          |Yes            |
+-----------------------+----------+-------------+---------------+

:sup:`1` - Both Book and Change services running on NIBS report into the same google analytics profile. At present the ability to differentiate usage at this level has not been investigated 

:sup:`2` - Service availability, while measured at the application level (NIBS) is the same for both Book and Change transactions and so not mis-leading if presented on respective transaction dashboards ain addition to the overview dashboard

Compared to the initial metrics requirements from Martin during the discovery phase, two metrics cannot not be supported on the platform at present:

* Time taken for transaction stages
* Browser usage

Technical analysis
==================
The purpose of the technical analysis phase is to work out the most appropriate sources of data for the metrics to be presented on 
the proposed dashboards. As well as identifying the sources of the data, this phase determines how the data can be propagated 
into the performance platform and any non-functional issues that need to be addressed e.g. the periodicity of data collection 
and the security requirements around the data itself.

The diagram below shows the key components of the DVSA service along with identified integrations for propagating data into the platform.

.. image:: dvsa-practical-driving-test-architecture.png

Mapping services and channels
-----------------------------

Mapping services and channels provides the contextual of the view of the service and how it is presented to users as well as where 
the specific set of dashboards sit in the context of how the organization operates the services. Understanding this context allows 
for a more flexible model for collecting and storing data to support the required dashboards

+------------------------+-----------+----------------------+-----------+---------------------+
|Organisational service  |Sector     |Transactional service |Channel    |Digital/non-digital  |
+========================+===========+======================+===========+=====================+
|Practical driving test  |Public     |Book                  |Online     |Digital              |
|                        |           |                      +-----------+---------------------+
|                        |           |                      |Telephone  |Non-digital          |
|                        |           |                      +-----------+---------------------+
|                        |           |                      |Post       |Non-digital          |
|                        |           +----------------------+-----------+---------------------+
|                        |           |Change                |Online     |Digital              |
|                        |           |                      +-----------+---------------------+
|                        |           |                      |Telephone  |Non-digital          |
|                        +-----------+----------------------+-----------+---------------------+
|                        |Business   |Book                  |Online     |Digital              |
|                        |           |                      +-----------+---------------------+
|                        |           |                      |Telephone  |Non-digital          |
|                        |           +----------------------+-----------+---------------------+
|                        |           |Change                |Online     |Digital              |
|                        |           |                      +-----------+---------------------+
|                        |           |                      |Telephone  |Non-digital          |
+------------------------+-----------+----------------------+-----------+---------------------+

Performance Data sources
------------------------

DVSA MI Mainframe
^^^^^^^^^^^^^^^^^

* The DVSA MI mainframe is capable of generating a periodic Practical driving test channel volumetrics report outlining the number of book and change transaction requests for both the public and business services and the channels over which the transaction took place.
* The report is generated by a legacy reporting tool – Crystal Reports
* The cost of integration from the mainframe discounted a direct integration approach in the timeframe agreed. This led to a manual upload of volumetrics data approach. The next challenge was to transform the data from its native Crystal Reports format to the defined Performance Platform format.
* A simple excel based ‘transformer’ was created to allow the service manager to convert the data themselves to the required format for manual upload to the platform.

Google Analytics
^^^^^^^^^^^^^^^^
**NIBS users**

* The NIBS application has been instrumented with Google Analytics, it was agreed the number of users accessing the service should be captured using the Performance Platforms GA real-time collector.
* An issue in the way the practical driving test analytics has been instrumented (shared GA profile for both ‘Book’ and ‘Change’ transactions) meant the number of users active on the Book or Change journey at any time could not be determined at the time.

**NIBS user journey data**

* User journey data recorded in Google Analytics from the NIBS application (running in the users browser) allows specific event data to be stored. 
* Martin and his team agreed to implement Performance Platform specific journey events (focusing on the process rather than the implementation structure of the application).
* Capturing this information allows the platform to capture completion rate of users undertaking the booking or change journey and the numbers of users at specific stages in the journey.
* To enable the above, the NIBS application needed performance specific events embedding in the application – see implementation

Embedding additional eventing information is an ‘intrusive’ integration as the performance platform required the DVSA development team to make changes to their application

**NIBS user journey help data**

* Part of Martin’s requirement was to see how dependent user were on the inline help features the application required
* It was agreed this information would be best captured by extending the above eventing scheme – see implementation

Pingdom
^^^^^^^
* The current performance platform mechanism for determining a services availability and response time is through the use of <Pingdom>.
* To support service availability metrics on the dashboard, the platform needed a non-user facing ‘pingable’ url available on the NIBS application.
* This url was configured on the performance platforms Pingdom account and results read via the Pingdom collector.
* This is an ‘intrusive’ integration as the performance platform required the DVSA development team to make changes to their application

GOV.UK
^^^^^^
* GOV.UK has an existing feed into the performance platform ensuring all user satisfaction survey quantitive data (non-narrative) is captured.
* Data is based on user feedback from the GOV.UK service ‘done’ page and provided as a <likert> scale. (1-5 ) measure.

Mapping service implementation
------------------------------
Understanding the services in scope in terms of the underlying IT systems allows identification of suitable source of data

+------------------------+-----------+----------------------+-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|Organisational service  |Sector     |Transactional service |Channel    |Digital/non-digital  |gov.uk start/end page                            |GOV.UK MI |Webapp     |DVSA MI        |Service GA profile |
+========================+===========+======================+===========+=====================+=================================================+==========+===========+===============+===================+
|Practical driving test  |Public     |Book                  |Online     |Digital              | | start: /book-practical-driving-test           |Yes       |NIBS       |DVSA Mainframe |Yes                |
|                        |           |                      |           |                     | | end: /done/book-practical-driving-test        |          |           |               |                   |
|                        |           |                      +-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |           |                      |Telephone  |Non-digital          |*n/a*                                            |*n/a*     |*n/a*      |DVSA Mainframe |*n/a*              |
|                        |           |                      +-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |           |                      |Post       |Non-digital          |*n/a*                                            |*n/a*     |*n/a*      |DVSA Mainframe |*n/a*              |
|                        |           +----------------------+-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |           |Change                |Online     |Digital              | | start: /change-date-practical-driving-test    |Yes       |NIBS       |DVSA Mainframe |Yes                |
|                        |           |                      |           |                     | | start: /cancel-practical-driving-test         |          |           |               |                   |
|                        |           |                      |           |                     | | end: /done/change-date-practical-driving-test |          |           |               |                   |
|                        |           |                      +-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |           |                      |Telephone  |Non-digital          |*n/a*                                            |*n/a*     |*n/a*      |DVSA Mainframe |*n/a*              |
|                        +-----------+----------------------+-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |Business   |Book                  |Online     |Digital              |*n/a*                                            |*n/a*     |OBS        |DVSA Mainframe |No                 |
|                        |           |                      +-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |           |                      |Telephone  |Non-digital          |*n/a*                                            |*n/a*     |*n/a*      |DVSA Mainframe |*n/a*              |
|                        |           +----------------------+-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |           |Change                |Online     |Digital              |*n/a*                                            |*n/a*     |OBS        |DVSA Mainframe |No                 |
|                        |           |                      +-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+
|                        |           |                      |Telephone  |Non-digital          |*n/a*                                            |*n/a*     |*n/a*      |DVSA Mainframe |*n/a*              |
+------------------------+-----------+----------------------+-----------+---------------------+-------------------------------------------------+----------+-----------+---------------+-------------------+

Mapping metrics to datatype to data source
------------------------------------------
Once data sources have been identified for the services in scope for the dashboards, the metrics identified in the business analysis stage need 
to be mapped via the required `datatype`_ onto their source. 

This activity additionally identifies how source data can be grouped (aggregated). This follows the principle of keeping a <datasets> scope 
as large as possible (holding data from more than one source as long as it shares the same `datatype`_) as long as each data record from each 
source can be uniquey identified.

As well as capturing the level at which data can be aggregated from its sources, the ‘level’ at which data can be presented on a dashboard 
can be determined. This reflects at what position in the service hierarchy the data is both valid and accurate in terms of the performance 
of the service.

================================ ======================== =================== ======================= ======================
Metric                           datatype                 data source         dataset grouping        dashboard level
================================ ======================== =================== ======================= ======================
**Live service usage**           realtime                 Service GA profile  Sector                  Sector
**Breakdown by service**         transactions by channel  DVSA mainframe      Organisational service  Transactional service
**User device type**             device usage             Service GA profile  Sector                  Sector
**Service availability**         monitoring               NIBS (via pingdom)  Sector                  Sector
**Transactions by channel**      transactions by channel  DVSA mainframe      Organisational service  Transactional service
**User satisfaction**            user satisfaction        GOV.UK              Transactional service   Transactional service
**Digital take-up**              transactions by channel  DVSA mainframe      Organisational service  Transactional service
**Completion rate**              user journey             Service GA profile  Sector                  Transactional service
**Users at each stage**          user journey             Service GA profile  Sector                  Transactional service
**Help usage**                   user journey help        Service GA profile  Sector                  Transactional service
================================ ======================== =================== ======================= ======================

Identifying the metrics and dashboards
--------------------------------------

The last activity in the analysis phase is to determine which metrics can be supported on which dashboard.

As identified in the Business analysis section of this study, three dashboards were identified with metrics presented on each appropriate to the level of detail that can be gathered from the identified data sources.

Practical driving tests (for public users)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Live service usage
* Breakdown by service
* User device type
* Service availability

Practical driving test bookings 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Transactions by channel
* User satisfaction
* Digital take-up
* Completion rate
* Users at each stage
* Help usage
* Service availability

Practical driving test changes and cancellations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Transactions by channel
* User satisfaction
* Digital take-up
* Completion rate
* Users at each stage
* Help usage
* Service availability

Implementation responsibilities
===============================

Following agreement on the metrics that can be supported and the dashboards required to present these for the service, implementation responsibilities were determined.

============================================================= ========= ============== ====================================================
Activity                                                      DVSA team Platform team  Notes
============================================================= ========= ============== ====================================================
Generate monthly report on channel volumetrics                Yes       No             Standard report via Crystal Reports
Build converter for volumetrics to platform format            No        Yes            Deliver as Excel macro
Define and agree scheme for process eventing in user journey  Yes       Yes
Implement user journey eventing in NIBS application           Yes       No
Implement ‘pingable’ url for service availability monitoring  Yes       No
Configure datasets on performance platform                    No        Yes
Configure GA collectors                                       No        Yes
Configure GA realtime collectors                              No        Yes
Configure Pingdom collector                                   No        Yes
Setup GOV.UK user satisfaction receiver                       No        Yes            Work with GOV.UK team to ensure direct push of data
Create dashboard configurations                               No        Yes
Create links to Platform homepage                             No        Yes
Create dashboard text content                                 Yes       Yes            Standard text with clarification from DVSA
Setup access to file upload facility for volumetrics report   No        Yes
Configure collector run times                                 No        Yes
============================================================= ========= ============== ====================================================

.. _datatype: ../data-architecture/datatype/index.html
