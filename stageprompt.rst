.. _stageprompt:

Stageprompt
===========

**Stageprompt** is a small javascript library which helps instrument
a user journey. It does not provide the analytics - you will need an
analytics provider such as Google Analytics or Piwik - but:

- It is easier to install on events than native Google Analytics
- It gives you an abstraction layer in case you change analytics providers in future
- It provides a controlled vocabulary which allows you to compare your user journey with others more easily

Stageprompt is the 'glue code' for integrating the page with the analytics provider
allowing you to easily record events such as *user loads page x* or *user opens inline
help module y*

The events which Stageprompt captures are stored by the analytics provider. For example
when integrating with Google Analytics events are sent using `Google's event tracking API`_.

For code and instructions on how to use Stageprompt see the `Github repo and readme`_.

.. _Google's event tracking API: https://developers.google.com/analytics/devguides/collection/gajs/eventTrackerGuide
.. _Github repo and readme: https://github.com/alphagov/stageprompt


When to use Stageprompt
-----------------------

Dependencies:

- An analytics service which provides event tracking (for example Google Analytics)
- jQuery

Considerations:

Stageprompt is designed to provide a basic level of user journey tracking and to record 
this data in a way consistent with other government transactions. It integrates well with 
the Performance Platform.

It can be added to a site with minimal development effort providing an analytics provider
is already set up. A javascript file must be included on each page where it is used and 
the html of the user journey will need to be tagged.

If a user journey has already been instrumented then Stageprompt may not be required; however,
if the journey has not yet been instrumented then Stageprompt is a good choice.
