README
======

This page provides general information for developers who want to work on and contribute to the *Airinnova* Python packages.

* https://github.com/airinnova

Repository structure
--------------------

All repositories have a standardised file structure which closely follows the structure proposed and described here:

* https://www.kennethreitz.org/essays/repository-structure-and-python

Every repository contains different folders:

* **src/** All source code related to the particular project. The *src* folder may contain subdirectories to distinguish between library and executables.

    * **lib/** Library code
    * **bin/** Executable files. On Linux such file would typically be found in `/usr/bin`.

* **docs** Complete project documentation.
* **tests** Complete set of test cases/code verification.

Dependencies
------------

Every Python package may depend on *external* packages which are not part of the Python standard library. Additional packages are also required to build the documentation and to run the testing framework. All external dependencies are listed in a file called `requirements.txt` located in the repository root folder. All requirements may be simply installed with the Python package installer pip:

.. code::

    pip install -r requirements.txt

**TODO** Note for pip

**Note** It is highly recommended to develop each Python package in a separate *virtual environment*

Development environment
-----------------------

* Git/Github
* Virtual environments

Testing
-------

PyTest, Tox, TravisCI

Local testing
~~~~~~~~~~~~~

Online testing
~~~~~~~~~~~~~~

PyTest
~~~~~~~

* https://docs.pytest.org/en/latest/

Tox
~~~

* https://tox.readthedocs.io/en/latest/

TravisCI
~~~~~~~~

* https://travis-ci.org/

Documentation
-------------

RST, Sphinx, ReadTheDocs

Sphinx
~~~~~~

* https://www.sphinx-doc.org/en/master/

ReadTheDocs
~~~~~~~~~~~

* https://readthedocs.org/

Packaging and code deployment
-----------------------------

PyPI, `setup.py`, `MANIFEST.in`

* https://pypi.org/

Miscellaneous
-------------

* Licences
