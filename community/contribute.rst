How to Contribute
==================
WEMEP is hosted in GitHub to become an open-source community project. For now, only invited participants from the Wakebench community are contributing to complete the first release.

These are some basic steps to get started when you are ready to contribute. 

#. Of course you need a `GitHub <https://github.com/>`_ account. It is through your username that the project tracks your contributions. 
#. Make a local copy of the WEMEP master repository. 

    .. code:: bash

      $ git clone https://github.com/windbench/WEMEP.git

#. Install the libraries that are needed to compile the docs.

    .. code:: bash

      $ pip install -r requirements.txt

#. Find the chapter you want to edit in the ``.rst`` files and edit it with your favorite text editor using `Sphinx <https://www.sphinx-doc.org/en/master/index.html>`_ syntax. 
#. Build the docs into a local html copy at ``/WEMEP/_build/html``

    .. code:: bash

      $ make html

#. You can now open your local copy of the WEMEP website (``/WEMEP/_build/html/index.html``) in your browser and see how your changes look like. 
#. Add and commit changes to the master repository with a short description (less than 50 characters) in the "Commit message" 

    .. code:: bash

      $ git add *
      $ git commit -m "Commit message"
      $ git push origin master

# `Read the Docs <https://readthedocs.org/>`_ takes care of hosting the WEMEP website. Your commit will be automatically build by RTD  





