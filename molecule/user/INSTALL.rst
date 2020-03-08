*******
Docker driver installation guide
*******

Requirements
============

* Docker Engine

Install
=======

Please refer to the `Virtual environment`_ documentation for installation best
practices. If not using a virtual environment, please consider passing the
widely recommended `'--user' flag`_ when invoking ``pip``.

.. _Virtual environment: https://virtualenv.pypa.io/en/latest/
.. _'--user' flag: https://packaging.python.org/tutorials/installing-packages/#installing-to-the-user-site

.. code-block:: bash

    $ pip install 'molecule[docker]'
    $ sudo apt-get -y install python-pip libssl-dev
    $ pip install --upgrade setuptools
    $ pip install ansible-lint
    $ pip install flake8
    $ pip install testinfra
    $ pip install molecule
    $ pip install molecule[docker]
    $ WDIR=$(pwd)
    $ cd /opt
    $ curl -L https://networkgenomics.com/try/mitogen-0.2.9.tar.gz | tar -xz
    $ cd $WDIR
