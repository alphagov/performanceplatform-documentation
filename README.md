
# Performance Platform Documentation

To build it locally make sure you have Sphinx_ installed. You can install it with pip::

  `pip install -r requirements.txt`

Once [Sphinx](http://sphinx-doc.org/) is installed the documentation can be built and served with make::

  `make html serve`

If you want to see your changes in realtime, you can install sphinx-autobuild::

  `pip install sphinx-autobuild`

Once sphinx-autobuild is installed, you can build the docs with this command:

  `sphinx-autobuild . ./_build/html`

And then visit the webpage served at [http://127.0.0.1:8000](http://127.0.0.1:8000). Each time a change to the documentation source is detected, the HTML is rebuilt and the browser automatically reloaded.

To stop the server simply press `^C`.
