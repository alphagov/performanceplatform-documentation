
# Performance Platform Documentaion

To build it locally make sure you have Sphinx_ installed. You can install it with pip::

  `pip install -r requirements.txt`

Once [Sphinx](http://sphinx-doc.org/) is installed the documentation can be built and served with make::

  `make html serve`

If you want to see your changes in realtime, you can install sphinx-autobuild::

  `pip install sphinx-autobuild`

Once sphinx-autobuild is installed, you can build the docs with this command:

  `sphinx-autobuild . ./_build/html`
