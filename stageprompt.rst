Stageprompt
===========

**StagePrompt** is a small javascript library for instrumenting a user journey
with an analytics provider (e.g. Google Analytics). The job of stage prompt is
to provide the 'glue code' for integrating the page with the analytics provider
allowing developers to easily record events such as *user loads page* or
*user opens inline help*.

The events which StagePrompt captures are stored by the analytics provider. For
example when integratin with Google Analytics events are sent using Google's
event tracking API: https://developers.google.com/analytics/devguides/collection/gajs/eventTrackerGuide.

For code and instructions on how to use StagePrompt see the Github repo and readme: https://github.com/alphagov/backdrop-send

When the use StagePrompt
========================

Dependencies:

- An analytics service which provides event tracking (for example Google Analytics)
- jQuery

Considerations:

Stageprompt is designed to provide a basic level of user journey tracking and to
record this data in such a way that the Performance Platform can easily retreive
and intepret it.

It can be added to a site with minimal development effort. A javascript file must
be included on each page where it is used and the html of the user journey will
need to be tagged.

If a user journey has already been instrumented by an inhouse development team
then StagePrompt may not be required. If, however, a basic level of user journey
tracking is required then StagePropt is a good choice.

