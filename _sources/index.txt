.. toctree::
    :maxdepth: 1
    :hidden:

    self
    api/write-api
    glossary


Get a Performance Dashboard
###########################

Get in touch
============

Email the performance team at `performance@digital.cabinet-office.gov.uk <mailto:performance@digital.cabinet-office.gov.uk>`_ to start.

The email must tell the team:

-	the name of your service
-	a short description of your service
-	the name and contact details of your service manager
-	whether you have access to developers who can help configure the dashboard
-	the name and contact details of these developers

You can still get a dashboard without help from developers. The performance team can help you through the process.

Without help from developers, your dashboard data won’t be automatically updated. You own the data in the dashboard and will be responsible for regularly maintaining its quality.


What happens next
=================

You’ll be invited to a meeting with the performance team to find out what data you already collect from your service. The team can also discuss how other data can be collected and how this data can be put into the dashboard.

Every performance dashboard must measure a service according to how:

- much it costs each person to use the service - known as 'cost per transaction'
- satisfied people feel when using the service - known as 'user satisfaction'
- likely people are to complete the service - known as the 'completion rate'
- many people use the service - known as ‘digital take-up’

You can choose from a number of other ways a dashboard can measure your service. You have the option to measure how:

- much help people need when using the service
- long it takes the service pages to load
- reliable the service’s servers are
- many people use the service online compared to by phone or in paper form


Get your data into a dashboard
==============================

There are 3 standard ways data can be put into a dashboard. You can choose to use just one or a mix of them all.

1. You can share your analytics data with the Performance Dashboard team - eg analytics data from Google Analytics, Omniture, or Piwik.

   The analytics data will be able to track how a service is used, eg how many people view a service online, complete an online application or access the service with their mobile phone.

   You can use :term:`Stageprompt <stageprompt>` when you share your analytics data. This provides a javascript wrapper around your data, so that if you change analytics provider in the future, you will not have to make changes to the connection you have with the Performance Platform.

2. Your developers can write code that automatically sends the latest data about your service to a dashboard (using the platform’s :doc:`write API <api/write-api>`). This will mean you don’t have to spend time manually updating spreadsheets.

   Contact `performance@digital.cabinet-office.gov.uk <mailto:performance@digital.cabinet-office.gov.uk>`_  to discuss getting access to the platform’s API.

3. Put your data in a spreadsheet and upload the spreadsheet to the performance dashboard website.  Ask the performance team for access to the admin user interface to do this.

   You’re responsible for regularly updating the spreadsheet with your latest data. Whenever your spreadsheet is updated, the dashboard will be updated. You’ll also be notified if the performance team expect new data to be uploaded by a certain date.


User satisfaction
=================

The last page of your service must link to the GOV.UK ‘done’ page where people are asked to complete a user satisfaction survey. The performance team can automatically add this feedback from the survey to your service dashboard.

Speak to your GOV.UK point of contact or service manager to get your service linked to the ‘done’ page if it’s not already. They should know the process and have the permissions to set up the link using the GOV.UK support form.


Service availability
====================

Your developers will need to supply the performance team with a ‘health-check’ URL from the service so the uptime and response time can be measured.

The performance team uses a website monitoring tool called Pingdom to constantly test the URL. All the data about your service’s availability will be automatically uploaded to the dashboard.


Presenting the dashboard data
=============================

The technical team will put together your service dashboard once you’ve decided on the data it will measure. The performance team has designers and user researchers who will work with you to figure out how best to present your data.

The performance team will give you a preview of your dashboard before it appears publically on the website.


Make corrections to dashboard data
==================================

Occasionally data in the dashboards may be incorrect. You can correct the data in your dashboard by:

- contacting the performance team if it’s data collected for you
- uploading the revised data to your spreadsheet - this will automatically display in the dashboard
