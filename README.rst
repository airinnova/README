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

**Note**

* It is highly recommended to develop each Python package in a separate *virtual environment* (see below).

3 Development environment
-------------------------

* Git/Github

It is highly recommended to develop each Python project in separate so-called *virtual environments*.
A virtual environments basically provides a working environment which is separate from the system-wide Python/Python library installation. All dependencies pertinent to the particular package which is being developed can be installed into the respective virtual environment. For more information on virtual environments see:

* https://docs.python.org/3/tutorial/venv.html
* https://virtualenvwrapper.readthedocs.io/en/latest/

4 Testing
---------

4.1 PyTest
~~~~~~~~~~

Test cases for each package can be found in the *tests* folder. We use the testing framework *pytest* which allows to set up test cases with relatively little effort. Test cases are defined in files which must be named ``test_*.py``, so for instance ``test_some_feature.py``. *pytest* will automatically locate these files and try to evaluate individual test cases. Each test cases is defined in a function named ``test_*()``.

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

5 Documentation
----------------

All documentation is included in the *docs* folder of the project. Documentation is built using the documentation generator *Sphinx*. The documentation is mainly written is RST (ReStructuredText). Documentation can be written manually, but API documentation can be generated automatically from *Python docstrings*.

The documentation can be converted into various format, e.g. PDFs or HTML websites. Project documentation can also be conveniently build and hosted on *readthedocs.org*.

* **RST** https://en.wikipedia.org/wiki/ReStructuredText
* **Sphinx** https://www.sphinx-doc.org/en/master/
* **ReadTheDocs** https://readthedocs.org/

6 Packaging and code deployment
-------------------------------

A Python project can be packaged which makes it easy to install and distribute. Two files, namely ``setup.py`` and ``MANIFEST.in`` (optional), located in the project root folder define how the package should look like. These file must follow a certain format. If set up correctly, a package may be installed by simply running ``pip install .`` in the same directory where ``setup.py`` is located.

* https://packaging.python.org/tutorials/

6.1 Python Package Index (PyPI)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Packaged Python projects can be distributed using the Python Package Index (PyPI). This makes it possible to install a Python package by simple running ``pip install pkg_name``.

* https://pypi.org/
* https://packaging.python.org/tutorials/packaging-projects/

6.2 Anaconda
~~~~~~~~~~~~

* https://anaconda.org/

7 Miscellaneous
---------------

7.1 Licensing
~~~~~~~~~~~~~

Projects should include a license file (``LICENSE.txt``) in the project root folder. More information on licenses can be found here:

* https://help.github.com/en/articles/licensing-a-repository
* https://choosealicense.com/

7.2 Code reuse
~~~~~~~~~~~~~~

Some projects make use of some quite general, common routines. To avoid having copies of same functions in different projects, common routines have been factored out and namespaced in the *CommonLibs* package.

* https://github.com/airinnova/commonlibs

Just beware that changing the interface of functions may affect the packages that use *CommonLibs*.
