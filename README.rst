Information for developers
==========================

This page provides general information for developers who want to work on and contribute to the *Airinnova* Python packages.

* https://github.com/airinnova

1 Repository structure
----------------------

All repositories have a standardised file structure which closely follows the structure proposed and described here:

* https://www.kennethreitz.org/essays/repository-structure-and-python

Every repository contains commonly used folders:

* **src** All source code related to the particular project. The *src* folder may contain subdirectories to distinguish between library code and executables.

    * **lib** Library code.
    * **bin** Executable files. On Linux such file would typically be found in `/usr/bin`.

* **docs** Complete project documentation.
* **tests** Complete set of test cases/code verification.

2 Dependencies
--------------

Every Python package may depend on *external* packages which are not part of the Python standard library. Additional packages are also required to build the *documentation* and to run the *testing framework*. All external dependencies are listed in a file called ``requirements.txt`` located in the repository root folder. All requirements may be simply installed with the *Python package installer* *pip*:

.. code::

    pip install -r requirements.txt

**See also**

* **pip** https://pip.pypa.io/en/stable/installing/

**Note** It is highly recommended to develop each Python package in a separate *virtual environment* (see below).

3 Development environment
-------------------------

3.1 Version control
~~~~~~~~~~~~~~~~~~~

*Git* is used as the *version control system* and code is hosted on *Github*.

* **Git** https://git-scm.com/doc
* **Github** https://github.com/

3.2 Virtual environments
~~~~~~~~~~~~~~~~~~~~~~~~

It is highly recommended to develop each Python project in separate so-called *virtual environment*.
A virtual environment basically provides a working environment which is separate from the system-wide Python/Python library installation. All dependencies pertinent to the particular package which is being developed can be installed into the respective virtual environment. For more information on virtual environments see:

* https://docs.python.org/3/tutorial/venv.html
* https://virtualenvwrapper.readthedocs.io/en/latest/

4 Testing
---------

4.1 PyTest
~~~~~~~~~~

Test cases for each package can be found in the *tests* folder. We use the testing framework *pytest* which allows to set up test cases with relatively little effort. Test cases are defined in files which must be named ``test_*.py``, so for instance ``test_some_feature.py``. *pytest* will automatically locate these files and try to evaluate individual test cases. Each test case is defined in a function named ``test_*()``.

.. code:: python

    def test_function_xyz():
        assert always_true() is True

To check all test cases defined in a folder *tests* we can simply run ``pytest tests/``. More information on *pytest*:

* https://docs.pytest.org/en/latest/

4.2 Tox
~~~~~~~

*Tox* is another tool related to testing. It can be used to bundle various tests defined in a file called ``tox.ini`` (root of project directory). See also:

* https://tox.readthedocs.io/en/latest/

4.3 Travis CI
~~~~~~~~~~~~~

Test cases defined with *PyTest* / *Tox* can be run locally. However, the code can also be tested automatically in the background using the continuous integration service *Travis CI*. If some test fails, it is possible to get notified with an email. The configuration file for *Travis CI* is called ``.travis.yml`` (root of project directory). See also:

* https://travis-ci.org/

**Note** Open-source projects are tested on *travis-ci.org*, not *travis-ci.com*.

4.4 Code coverage
~~~~~~~~~~~~~~~~~

When testing with *pytest* it is possible to create a report which show which parts of the code base have been executed and which haven't. This can be a help in identifying parts of the code base which are not yet tested. To generate a *coverage report* with *pytest* a plug-in called *pytest-cov* can be used. Coverage results can also be displayed nicely on *Codecov.io*.

* *pytest-cov* https://pytest-cov.readthedocs.io/en/latest/
* *Codecov.io* https://codecov.io/

**Note** The code coverage in percent is merely an indication of the testing status, but 100% test coverage does not imply that there are not any bugs.

5 Documentation
----------------

All documentation is included in the *docs* folder of the project. Documentation is built using the documentation generator *Sphinx*. The documentation is mainly written is *RST* (*ReStructuredText*). Documentation can be written manually, but API documentation can be generated automatically from *Python docstrings*.

The documentation can be converted into various format, e.g. PDFs or HTML websites. Project documentation can also be conveniently built and hosted on *readthedocs.org*.

* **RST** https://en.wikipedia.org/wiki/ReStructuredText
* **Sphinx** https://www.sphinx-doc.org/en/master/
* **ReadTheDocs** https://readthedocs.org/

6 Packaging and code deployment
-------------------------------

A Python project can be packaged which makes it easy to install and distribute. Two files, namely ``setup.py`` and ``MANIFEST.in`` (optional), located in the project root folder define how the package should look like. These files must follow a certain format. If set up correctly, a package may be installed by simply running ``pip install .`` in the same directory where ``setup.py`` is located.

* https://packaging.python.org/tutorials/

6.1 Python Package Index (PyPI)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Packaged Python projects can be distributed using the *Python Package Index* (*PyPI*). This makes it possible to install a Python package by simple running ``pip install pkg_name``.

* https://pypi.org/
* https://packaging.python.org/tutorials/packaging-projects/

7 Miscellaneous
---------------

7.1 Licensing
~~~~~~~~~~~~~

It is good practice to include a license file (``LICENSE.txt``) in the project root folder. More information on licenses can be found here:

* https://help.github.com/en/articles/licensing-a-repository
* https://choosealicense.com/

7.2 Code reuse
~~~~~~~~~~~~~~

Some projects make use of some quite general, common routines. To avoid having copies of same functions in different projects, common routines have been factored out and namespaced in the *CommonLibs* package.

* https://github.com/airinnova/commonlibs

Just beware that changing the interface of functions may affect the packages that use *CommonLibs*.

7.3 CPACS and Anaconda
~~~~~~~~~~~~~~~~~~~~~~

The use of *CPACS* requires two libraries developed by DLR, namely *Tigl* and *Tixi*. Unfortunately, these libraries are not available on the official Python Package Index (PyPI). Thus, they cannot be installed via the `requirements.txt` file. However, the DLR provided packages via *Anaconda* which creates its own environments separate from the standard Python virtual environments.

For testing and development, the use of *Tigl* and *Tixi* via *Anaconda* has proven itself to be the most reliable option. For testing on *Travis CI*, there is also a light-weight version of *Anaconda* called *Miniconda*.

* **Tigl** https://github.com/DLR-SC/tigl
* **Tixi** https://github.com/DLR-SC/tixi
* **Anaconda** https://www.anaconda.com/
* **Miniconda** https://docs.conda.io/en/latest/miniconda.html

Currently, only **PyTornado** uses *Tigl* and *Tixi*. See the file ``environment.yml`` (Anaconda environment definition).
