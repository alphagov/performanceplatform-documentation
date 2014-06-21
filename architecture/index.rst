.. _architecture:

Architecture
############

The performance platform is made of several separate apps.

- **Collectors** take your data and feed it into the performance platform
- **Backdrop** stores data and lets you retrieve it using standardised commands
- **Spotlight** displays your data in a dashboard, using a range of module designs

.. image:: https://docs.google.com/drawings/d/1Kmz0PIsozcMSef-CoBRkx7jexoqEHbSHbdHO-H07WTM/pub?w=960&amp;h=720

Data Flows
==========

Currently, data goes in, is stored, and data is transformed on the way out. We expose a reasonably rich query API in the alpha version.

In the future we'd like to move toward transforming data as it is stored. We'd like to do the CPU-intensive work early on, and trade off increased storage at write time for faster responses at read time.

Backdrop -- HTTP API for persistence and querying
=================================================

https://github.com/alphagov/backdrop

Backdrop provides the write and read API for our data store (currently mongodb).

Spotlight -- rendering layer
============================

https://github.com/alphagov/spotlight

Spotlight provides a lightweight rendering layer which provides:

* modules
* dashboards (a collection of modules)

Stagecraft -- configuration API
===============================

https://github.com/alphagov/stagecraft

Stagecraft provides an API and UI for managing backdrop datasets.

Stageprompt -- Analytics adapter
================================

**Stageprompt** is a small javascript library which helps instrument
a user journey. It does not provide the analytics -- you will need an
analytics provider such as Google Analytics or Piwik -- but it:

- is easier to install on events than native Google Analytics
- gives you an abstraction layer in case you change analytics providers in future
- provides a controlled vocabulary which allows you to compare your user journey with others more easily

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

.. toctree::
  :maxdepth: 2

  data-flows
  parts/index
