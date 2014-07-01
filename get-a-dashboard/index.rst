
Get a dashboard
###############

Get in touch
============

.. To get a dashboard, just answer these 3 questions:

.. 1. Foo?
.. 2. Bar?
.. 3. Foo, bar?

Email us at `performance@digital.cabinet-office.gov.uk <mailto:performance@digital.cabinet-office.gov.uk>`_

.. Deliberately not mentioning the ten onboarding questions here to reduce friction.
.. Instead, we should put just a couple of questions to reduce friction further.

What happens next?
==================

We'll set up a meeting with you to discuss your needs. Our technical and business analysts will help you find out what data you already, what data we could help you collect and how we can get this data into our systems.

We need to get data from the service into the performance platform. Typically we can work with your existing web analytics, CSV exports and legacy systems. We might ask for some small code changes. Our technical team can help you automate data collection.

Once we've got some data to work with, our developers will put together a dashboard for your service. Our design and user research team will work with you to figure out how best to present your data.

We'll give you a preview of your dashboard before it goes live using our staging environment, and you'll have a chance to write a blog post if you want to.

Integrating
===========

To use the performance platform, you have to get data about your system
in to the performance platform. There are currently 3 ways to do this:

#. Grant access to your data to the performance platform team
   and allow us to pull data in about your system.
#. Have your developers write code that will regularly send the latest
   information about the service to the performance platform, using our
   API
#. Manually upload data to the performance platform via the admin UI

The depth of your integration might depend on the capabilities, people
and budget available to you. Do you have people with the skills to
write code / instrument you service, or can you go to market to get
them?

Pulling data
============
This is the fastest way to get data onto the performance platform. We
can run various collectors which will pull data about your service into our database.

Analytics
---------
You can share analytics data, such as from Google Analytics, Omniture
or Piwik. We can use this to track how a service is used, including how
many people:

- view a service online
- start completing an online application
- finish completing a service online

When instrumenting your site we recommend you use :ref:`Stageprompt <stageprompt>`.
This provides a wrapper around your analytics provider, so that if you
change provider in the future, you should not have to make changes to
continue to report data to the performance platform.

Response times
--------------
We can track page response times and service availability for you.

Pushing data
============

This documentation contains guides to the technology behind the
performance platform and :doc:`how to integrate with it </send-to-backdrop/index>`.
Your development team should contact the performance platform team
before they start writing the code.

Manual upload
=============

You can put your data in a spreadsheet and upload the spreadsheet to
the Performance Dashboard website.

.. note::

  You are responsible for regularly updating the spreadsheet with your
  latest data. Whenever your spreadsheet is updated, the dashboard will
  be updated.

  We have a roadmap item to look at sending you notifications when we
  are expecting data to be uploaded and we haven't seen it yet.

.. _corrections:

Making corrections
==================
Occasionally mistakes will happen. Data in a system may be incorrect.
The performance platform currently treats any incoming data as the new,
correct version for a given time period. So if data needs correcting,
you can get the data corrected by contacting the performance platform
if it's something that we collect, or you can push/upload the revised
data and the update will automatically display.

.. toctree::
   :maxdepth: 2
   :hidden:

   sending-data-to-backdrop


