
Update
================

Upate code
~~~~~~~~~~~

1. Go to *ICCLIM* working directory

2. View modified files:

.. code-block:: sh

    $ git status
    
3. Add modified file(s):

.. code-block:: sh
    
    $ git add f1 f2 f3
    
4. Commit modifications:

.. code-block:: sh

    $ git commit -m "Modifications description"
    
5. Push to the remote repository:

.. code-block:: sh

    $ git push
    
6. Repeat steps 3-4-5 if needs until:

.. code-block:: sh

    $ git status
    
    # On branch master
    nothing to commit (working directory clean)





Update documentation
~~~~~~~~~~~~~~~~~~~~~

ICCLIM documentation is generated by `Sphinx <http://sphinx-doc.org/>`_

To update the documentation:

1. Go to icclim/icclim/icclim_doc/source/

2. Modify .rst files

3. Run:

.. code-block:: sh

    $ make html

4. "git add-commit-push" 


Update version
~~~~~~~~~~~~~~~

Change ICCLIM version number in following files:

1. In icclim/**setup.py**

2. In icclim/icclim/**__init__.py**

3. In icclim/icclim/icclim_doc/source/**conf.py**

Then "git add-commit-push"
