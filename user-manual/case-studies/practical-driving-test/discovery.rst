Discovery
#########

The discovery phase covers the initial engagement with the government organization, capturing data about 
how the service operates and identifying initial dashboard metrics that would most assist the service 
manager in improving the service.

This phase captures information about:

* how the service is accessed and presented to users
* how the service is managed by the organization
* where the identified service sits in context with other associated services
* identifying the metrics that would add value to the Service Manager in improving the user experience and efficiency of the service
* understanding the underlying systems architecture and how it supports users

The discovery phase was initiated with a meeting between the performance platform team and the service 
delivery team at what was then the Driving Standards Agency (DSA).  

The Performance Platform was in an early stage of its development and Martin had offered to help shape 
the features of the platform using the practical driving test service as a candidate client. 
 
Initial scope
*************
It was decided at an early stage to focus on the practical driving test service offered to members of the public.  

This service handles the larger volume of transactions, had recently been migrated onto a new application and 
had already been instrumented using Google Analytics (a primary source of performance data).  

Constraints
===========

* The practical driving test itself is dependent on the type of vehicle the user selects.  It was agreed at this stage the vehicle type was out-of-scope.
* The change/cancel service has a number of types/options for change that the user can select. For the initial dashboard, the specific change the user selects within the service was out of scope
* The implementation of the dashboards and underpinning storage of data should be geared to allowing extension at a later date to include dashboards for the other service options and user types 

User experience
***************
The service is accessed by users from the main <GOV.UK> site:

* Book:     https://www.gov.uk/book-practical-driving-test
* Change:   https://www.gov.uk/change-date-practical-driving-test
* Cancel:   https://www.gov.uk/cancel-practical-driving-test

Support for Welsh language users is also available for bookings:

https://www.gov.uk/archebu-prawf-gyrru-ymarferol

Booking a practical driving test
================================

User are redirected from GOV.UK to the ‘Book your practical driving test’ start screen at:

https://driverpracticaltest.direct.gov.uk/application?execution=e1s1

The users journey is linear (all stages completed in sequence) and is split into a number of stages.  Users are required to complete all sections and pay for their test.

#. Choose the type of vehicle test
#. Enter their licence details
#. Select a test centre
#. Choose a time and date for their test
#. Enter their details
#. Enter their payment details
#. Confirm their information and pay
#. Receive confirmation of their booking

On completion, users are redirected back to GOV.UK where they can opt to complete a user satisfaction survey:  

https://www.gov.uk/done/book-practical-driving-test

Change/cancel a practical driving test
======================================

Users are redirected from both GOV.UK  start pages to the ‘Change your practical driving test’ start screen at:  

https://driverpracticaltest.direct.gov.uk/login

The first user journey stage is to enter their driving licence number and application reference number.  Following validation, the user is able to make individual changes to their booking or cancel it.  Activities users can undertake can include:

* checking a booking
* changing the type of test
* changing vehicle details
* changing special requirements
* changing instructor reference number
* changing test centre
* changing the time and date of the test
* cancelling the test

On completion, users are redirected back to GOV.UK where they can opt to complete a user satisfaction survey:  

https://www.gov.uk/done/change-date-practical-driving-test

Service context
***************
The context of the Book and Change transactional services offered as part of the broader set of DVSA services can be seen below.

.. image:: dvsa-practical-driving-test-context.png

Technical architecture
**********************
The IT systems relevant to the in scope services are: 

GOV.UK
======
* Individuals wanting to either book or change their practical driving test start their journey on the GOV.UK site
* Users are redirected from GOV.UK pages to the respective DVSA webapps (see below)
* On completion of the user journey, users are redirected to GOV.UK and have the option of completing a user satisfaction survey
* The site hosts the user satisfaction survey and can provide aggregated quantitative results of completed surveys to the performance platform
* GOV.UK has been instrumented for Google Analytics (GA) 

New Internet Booking System (NIBS)
==================================
* NIBS is a DVSA hosted system and presents all practical driving test services to public users.
* NIBS manages both bookings and changes within the same webapp – users entering via separate start pages dependent on their need.
* NIBS has been instrumented for GA with user/page and event data captured in GA directly from user browser sessions

Online Booking System (OBS)
---------------------------

* OBS is a DVSA hosted system and presents all practical driving test services to business users.
* OBS was considered out of scope for this part of the engagement 

DVSA Management Information mainframe
-------------------------------------

* Management Information data for the practical driving test service is stored on a DVSA legacy mainframe.
* The mainframe holds information for practical driving across all services and channels.
* Reports are produced from data held in the mainframe via a legacy Crystal Reports application

Google Analytics
----------------

* Analytics data generated during user’s browser sessions whiel using the NIBS application are sent to a single GA profile for both bookings and changes

Metrics
=======
Discussion identified which metrics would prove useful to Martin in spotting opportunities for improvements to the service.
Those metrics being:

* User volumes across the online user journey – providing insight into where users drop out, rely on ‘help’ and completion rates to identify where the journey can be improved
* How users access the service – understanding what types of device and browsers are used for which types of activity to enable focusing the user experience to user preferences
* Volumetrics – tracking use of the service via online and offline channels to allow long term trend spotting and to act as a ‘single source of truth’ 
* Time on transactions – to identify where in the process users are spending longer amounts of time in order to identify where improved guidance should be provided 

The service team expressed a need that separate dashboards will be created for public and business facing services and that focus should be on the public service in the first instance. 

Existing dashboards
===================
The work within this study covers the first dashboards for the practical driving test based on data derived directly from the service implementation. The DVSA already has the following ‘high volume transaction dashboards’ available on the performance platform:

Practical driving test: bookings https://www.gov.uk/performance/dft-book-practical-driving-test
Practical driving test: changes to bookings https://www.gov.uk/performance/dft-amend-practical-driving-test

The data supporting these dashboards is provided by Martin and team and is an overarching set of costs and volumes across both public and business facing variants of the service.

It was decided that at present it would be misleading to present these metrics as part of the public facing service dashboards and a potential higher level dashboard would be a benefit to Martin and his team at a later date.
