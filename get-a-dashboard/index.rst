Integrating
###########

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


