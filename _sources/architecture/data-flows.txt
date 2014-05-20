.. _data_flows:

Data Flows
##########

At the simplest view, data goes into the platform, is persisted and data comes out of the platform.

That wouldn't be a great deal of use, providing merely dumb persistence akin to a file system.

To make it more useful, we want some more functionality. Options include:

#. Data goes in, is transformed and persisted, then data comes out.
#. Data goes in, is persisted, data is transformed on the way out.
#. Data goes in, is transformed, persisted, and data is transformed on the way out.

We are currently using something like the second option. We expose a reasonably rich query API in the alpha version.

Longer term, we are looking to move to a model more like the first option. We would like to do the expensive work at ingestion time, and trade off increased storage at write time for faster responses at read time.
