Implementation
**************

Generate monthly report on channel volumetrics
==============================================

The service manager is responsible for producing regular reports on the volumes of transactions for all practical driving test transactions.
The report is created via Crystal eports from information held in the DVSA Mainframe.

The report is to be generated and data loaded into the performance platform on a monthly basis.

**Format:**

=========== =========== ========== ===== ============== =============
Date        Online book Phone book Post  Online changes Phone changes
=========== =========== ========== ===== ============== =============
01/01/2014  4000        1000       10    200            20
02/01/2014  4500        900        3     180            15
03/01/2014  4250        940        0     160            20
=========== =========== ========== ===== ============== =============

Build a converter for volumetrics to platform format
====================================================

The platform file upload facility supports a standard format file input. The platform team built a simple excel file converter 
for the service manager to use to convert the mainframe report into the right format.

The format was built to be extensible to allow input for business as well as public booking and change data across supported channels

**Output format:**

===================== ======== ========== ======== ======== ========
_timestamp            period   sector     action   channel  count
===================== ======== ========== ======== ======== ========
2014-03-01T00:00:00Z  day      public     book     online   3048
2014-03-01T00:00:00Z  day      public     book     phone    0
2014-03-01T00:00:00Z  day      public     book     post     0
2014-03-01T00:00:00Z  day      public     change   online   1403
2014-03-01T00:00:00Z  day      public     change   phone    0
2014-03-01T00:00:00Z  day      business   book     online   400
2014-03-01T00:00:00Z  day      business   book     phone    0
2014-03-01T00:00:00Z  day      business   change   online   109
2014-03-01T00:00:00Z  day      business   change   phone    0
===================== ======== ========== ======== ======== ========

Define and agree the journey eventing scheme
============================================

As the NIBS application is instrumented using Google Analytics, the DVSA team did not have any issues with implementing 
the <user journey eventing> scheme adopted by the platform. The team chose not to utilize the <Stageprompt> 
javascript library, having their own approach to embedding GA events to user journeys.

It was decided that the eventing scheme adopted should address both the primary user journey event capture and 
where users resorted to online help to assist them – see below.

The scheme followed the use of the GA eventCategory; eventAction and eventLabel approach.

**NOTE:**
It was decided at the time to leave the eventLabel blank when a user reached that stage in the journey – this approach has since been revised
In the eventCategory, the transaction ‘name’ was placed at the beginning of the string following the ‘pp-‘ prefix – this approach has also been revised

Book practical driving test event scheme
----------------------------------------

====================================== ================================================= ================================================
ga:eventCategory                       ga:eventAction                                    ga:eventLabel
====================================== ================================================= ================================================ 
pp-book-practical-driving-test-public  booking-complete
pp-book-practical-driving-test-public  booking-failure
pp-book-practical-driving-test-public  cannot-continue
pp-book-practical-driving-test-public  choose-alternative-test-centre                    help:more-about-placing-a-test-on-hold
pp-book-practical-driving-test-public  choose-alternative-test-centre                    help:why-cant-i-find-an-appointment
pp-book-practical-driving-test-public  choose-alternative-test-centre
pp-book-practical-driving-test-public  choose-available-test                             help:understanding-types-of-test
pp-book-practical-driving-test-public  choose-available-test
pp-book-practical-driving-test-public  choose-date-and-time                              help:choosing-a-test-date-and-time
pp-book-practical-driving-test-public  choose-date-and-time                              help:what-is-my-instructors-reference-number
pp-book-practical-driving-test-public  choose-date-and-time
pp-book-practical-driving-test-public  choose-test-centre
pp-book-practical-driving-test-public  choose-type-of-test
pp-book-practical-driving-test-public  confirm-all-details
pp-book-practical-driving-test-public  enter-date-of-birth
pp-book-practical-driving-test-public  enter-licence-details                             help:what-are-extended-tests
pp-book-practical-driving-test-public  enter-licence-details                             help:what-are-special-requirements
pp-book-practical-driving-test-public  enter-licence-details                             help:what-is-my-driving-licence-number
pp-book-practical-driving-test-public  enter-licence-details
pp-book-practical-driving-test-public  enter-payment-details                             help:what-is-my-card-security-code
pp-book-practical-driving-test-public  enter-payment-details
pp-book-practical-driving-test-public  enter-special-requirements-details
pp-book-practical-driving-test-public  enter-theory-test-number                          help:where-can-i-find-my-theory-test-pass-number
pp-book-practical-driving-test-public  enter-theory-test-number 
pp-book-practical-driving-test-public  enter-vehicle-details                             help:what-is-a-meeting-place
pp-book-practical-driving-test-public  enter-vehicle-details                             help:why-do-i-need-to-enter-the-number-of-cab-seats
pp-book-practical-driving-test-public  enter-vehicle-details                             help:why-do-i-need-to-enter-the-number-of-passenger-seats
pp-book-practical-driving-test-public  enter-vehicle-details                             help:why-do-i-need-to-enter-the-vehicle-height
pp-book-practical-driving-test-public  enter-vehicle-details                             help:why-do-i-need-to-enter-the-vehicle-length
pp-book-practical-driving-test-public  enter-vehicle-details                             help:why-do-i-need-to-enter-the-vehicle-width
pp-book-practical-driving-test-public  enter-vehicle-details
pp-book-practical-driving-test-public  enter-your-details                                help:why-does-the-dvsa-need-my-contact-number
pp-book-practical-driving-test-public  enter-your-details
pp-book-practical-driving-test-public  licence-details-extended-test
pp-book-practical-driving-test-public  page-not-found
pp-book-practical-driving-test-public  recaptcha-check
pp-book-practical-driving-test-public  the-practical-driving-test-service-isnt-available
pp-book-practical-driving-test-public  theres-been-a-problem-with-the-service.
pp-book-practical-driving-test-public  you-went-away-and-came-back-again
====================================== ================================================= ================================================

Change practical driving test event scheme
------------------------------------------

======================================== ================================================= ================================================
ga:eventCategory                         ga:eventAction                                    ga:eventLabel
======================================== ================================================= ================================================
pp-change-practical-driving-test-public  access-your-booking                               help:what-is-my-application-reference-number
pp-change-practical-driving-test-public  access-your-booking                               help:what-is-my-driving-licence-number
pp-change-practical-driving-test-public  access-your-booking                               help:what-is-my-theory-test-pass-number
pp-change-practical-driving-test-public  access-your-booking
pp-change-practical-driving-test-public  booking-failure
pp-change-practical-driving-test-public  cannot-continue
pp-change-practical-driving-test-public  change-booking
pp-change-practical-driving-test-public  change-instructors-reference-number               help:what-is-my-instructors-reference-number
pp-change-practical-driving-test-public  change-instructors-reference-number  
pp-change-practical-driving-test-public  change-special-requirements                       help:what-are-special-requirements
pp-change-practical-driving-test-public  change-special-requirements
pp-change-practical-driving-test-public  choose-alternative-test-centre                    help:why-cant-i-find-an-appointment
pp-change-practical-driving-test-public  choose-alternative-test-centre
pp-change-practical-driving-test-public  choose-available-test                             help:understanding-types-of-test
pp-change-practical-driving-test-public  choose-available-test
pp-change-practical-driving-test-public  choose-date-and-time                              help:choosing-a-test-date-and-time
pp-change-practical-driving-test-public  choose-date-and-time
pp-change-practical-driving-test-public  choose-test-centre
pp-change-practical-driving-test-public  choose-type-of-test
pp-change-practical-driving-test-public  confirm-cancellation
pp-change-practical-driving-test-public  confirm-changes
pp-change-practical-driving-test-public  email-address
pp-change-practical-driving-test-public  enter-payment-details                             help:what-is-my-card-security-code
pp-change-practical-driving-test-public  enter-payment-details
pp-change-practical-driving-test-public  enter-special-requirements-details
pp-change-practical-driving-test-public  enter-theory-test-number
pp-change-practical-driving-test-public  enter-vehicle-details                             help:why-do-i-need-to-enter-the-vehicle-length
pp-change-practical-driving-test-public  enter-vehicle-details
pp-change-practical-driving-test-public  enter-your-details                                help:why-does-the-dvsa-need-my-contact-number
pp-change-practical-driving-test-public  enter-your-details
pp-change-practical-driving-test-public  recaptcha-check
pp-change-practical-driving-test-public  there-was-a-problem-processing-your-refund 
pp-change-practical-driving-test-public  you-went-away-and-came-back-again  
pp-change-practical-driving-test-public  your-test-fee-will-be-refunded 
======================================== ================================================= ================================================

Implement ‘pingable’ url for service availability monitoring
============================================================

The DVSA development team were responsible for creating a ‘pingable’ test url page, not accessible as part of the user journey that allowed 
`Pingdom`_ checks to be made to assess whether the service was available (not including a redirect message page if it was not), and give in 
indicative response time for requests to the service (this required a check against the backend repository NIBS used rather than an 
immediate 200 ‘OK’ response)

**url:** *(withheld)*

Configure datasets on performance platform
========================================== 

The required datasets to support the metrics were identified and created on the performance platform. All attempts are made to maximize the 
scope of a given dataset and the naming convention adopted reflects the ‘level’ of the service aggregation.

External factors restricted the adoption of the naming convention for some datasets (user satisfaction)

+------------------------+-----------+----------------------+-----------------------------------+------------------------+------------------------------------------------------+
|Organisational service  |Sector     |Transactional service |datagroup                          |datatype                |dataset                                               |
+========================+===========+======================+===================================+========================+======================================================+
|Practical driving test  |*all*      |*all*                 |driving-test-practical             |transactions-by-channel |driving_test_practical_transactions_by_channel        |
|                        +-----------+----------------------+-----------------------------------+------------------------+------------------------------------------------------+
|                        |Public     |*all*                 |driving-test-practical-public      |realtime                |driving_test_practical_public_realtime                |
|                        |           |                      |                                   +------------------------+------------------------------------------------------+
|                        |           |                      |                                   |device-usage            |driving_test_practical_public_device_usage            |
|                        |           |                      |                                   +------------------------+------------------------------------------------------+
|                        |           |                      |                                   |monitoring              |driving_test_practical_public_monitoring              |
|                        |           |                      |                                   +------------------------+------------------------------------------------------+
|                        |           |                      |                                   |journey                 |driving_test_practical_public_journey                 |
|                        |           |                      |                                   +------------------------+------------------------------------------------------+
|                        |           |                      |                                   |journey-help            |driving_test_practical_public_journey_help            |
|                        |           +----------------------+-----------------------------------+------------------------+------------------------------------------------------+
|                        |           |Book                  |book-practical-driving-test        |juser-satisfaction      |book_practical_driving_test_user_satisfaction         |
|                        |           +----------------------+-----------------------------------+------------------------+------------------------------------------------------+
|                        |           |Change                |change-date-practical-driving-test |user-satisfaction       |change_date_practical_driving_test_user_satisfaction  |
+------------------------+-----------+----------------------+-----------------------------------+------------------------+------------------------------------------------------+

Configure GA collectors
=======================

The configurations of the collector for Google Analytics to populate identified `datasets`_ using are stored in the platforms publically accessible `git`_ repository

============================================ ======================================================================================================================================================
dataset                                      Configuration
============================================ ======================================================================================================================================================
driving_test_practical_public_device_usage   https://github.com/alphagov/performanceplatform-collector-config/blob/master/queries/driving-test-practical-public/device-usage.json
driving_test_practical_public_journey        https://github.com/alphagov/performanceplatform-collector-config/blob/master/queries/driving-test-practical-public/journey.json
driving_test_practical_public_journey_help   https://github.com/alphagov/performanceplatform-collector-config/blob/master/queries/driving-test-practical-public/journey-help.json
============================================ ======================================================================================================================================================

Configure GA realtime collectors
================================

The configurations of the collector for using the Google Analytics realtime api to populate identified `datasets`_ using are stored in the platforms publically accessible `git`_ repository

============================================ ======================================================================================================================================================
dataset                                      Configuration
============================================ ======================================================================================================================================================
driving_test_practical_public_monitoring     https://github.com/alphagov/performanceplatform-collector-config/blob/master/queries/driving-test-practical-public/realtime.json
============================================ ======================================================================================================================================================

Configure Pingdom collector
===========================

The configurations of the collector for Pingdom to populate identified `datasets`_ using are stored in the platforms publically accessible `git`_ repository

============================================ ======================================================================================================================================================
dataset                                      Configuration
============================================ ======================================================================================================================================================
driving_test_practical_public_monitoring     https://github.com/alphagov/performanceplatform-collector-config/blob/master/queries/driving-test-practical-public/monitoring.json
============================================ ======================================================================================================================================================

Setup GOV.UK user satisfaction receiver
=======================================

User satisfaction data derived from GOV.UK is 'posted' directly to a defined write api endpoint, the sender identified using a provided bearer token

====================================================== ======================================================= ========================================
dataset                                                Write api endpoint                                      Bearer token
====================================================== ======================================================= ========================================
book_practical_driving_test_user_satisfaction          /book-practical-driving-test/user-satisfaction          *provided to GOV.UK development team*
change_date_practical_driving_test_user_satisfaction   /change-date-practical-driving-test/user-satisfaction   *provided to GOV.UK development team*
====================================================== ======================================================= ========================================

Configure collector run times
=============================

Collectors are scheduled to run at specific intervals. Run times are managed via a cronjob operating on the platform.

Configuration links: https://github.com/alphagov/performanceplatform-collector-config/blob/master/cronjobs

Create dashboard configurations and text content
================================================

Dashboard configuration including layout, visualisation and text are managed currently in the team and reviewed by the Service Manager. 

The configurations are stored in the platforms publically accessible `git`_ repository

================================================== ==============================================================================================================================================
Dashboard                                          Configuration file
================================================== ==============================================================================================================================================
Practical driving tests                            https://github.com/alphagov/spotlight/blob/master/app/support/stagecraft_stub/responses/experimental/practical-driving-test.json
Practical driving test bookings                    https://github.com/alphagov/spotlight/blob/master/app/support/stagecraft_stub/responses/experimental/book-practical-driving-test.json
Practical driving test changes and cancellations   https://github.com/alphagov/spotlight/blob/master/app/support/stagecraft_stub/responses/experimental/change-practical-driving-test.json
================================================== ==============================================================================================================================================

.. _datasets: ../data-architecture/dataset/index
.. _git: http://git-scm.com/
