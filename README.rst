######
wp2markdown-soube
######

这是个基于Exitwp的工具，用来把wordpress的blog转为markdown格式，和Exitwp不同的是p这个工具生成的文章元数据格式更简洁。

Runtime dependencies
====================
 * `Python <http://python.org/>`_ 2.6, 2.7, ???
 * `html2text <http://www.aaronsw.com/2002/html2text/>`_ :  converts HTML to markdown (python)
 * `PyYAML <http://pyyaml.org/wiki/PyYAML>`_ : Reading configuration files and writing YAML headers (python)
 * `Beautiful soup <http://www.crummy.com/software/BeautifulSoup/>`_ : Parsing and downloading of post images/attachments (python)


Installing dependencies in ubuntu/debian
----------------------------------------

   ``sudo apt-get install python-yaml python-bs4 python-html2text``

Installing Python dependencies using python package installer (pip)
-------------------------------------------------------------------

From the checked out root for this project, type:

   ``sudo pip install --upgrade  -r pip_requirements.txt``

Note that PyYAML will require other packages to compile correctly under ubuntu/debian, these are installed by typing:

   ``sudo apt-get install libyaml-dev python-dev build-essential``

Using Vagrant for dependency management
---------------------------------------

In the event your local system is incompatible with the dependencies listed (or you'd rather not install them), you can use the included Vagrantfile to start a VM with all necessary dependencies installed.

1. Lint and place all wordpress xml files in the ``wordpress-xml`` directory as mentioned above
2. In the directory of the unzipped archive, run ``vagrant up``.
3. SSH to your Vagrant VM using ``vagrant ssh``
4. Run ``cd /vagrant`` to open the VM's shared folder
5. Run the converter from the VM by typing ``python run.py``
6. After the converter completes, exit the SSH session using ``exit``
7. You should now have all the blogs converted into separate directories under the ``build`` directory
8. **Important:** Once satisfied with the results, run ``vagrant destroy -f`` to shut down the VM and remove the virtual drive from your local machine

Configuration/Customization
===========================

See the `configuration file <https://github.com/thomasf/exitwp/blob/master/config.yaml>`_ for all configurable options.

Some things like custom handling of non standard post types is not fully configurable through the config file. You might have to modify the `source code <https://github.com/thomasf/exitwp/blob/master/exitwp.py>`_ to add custom parsing behaviour.

Known issues
============
 * Target file names are some times less than optimal.
 * Rewriting of image/attachment links if they are downloaded would be a good feature
 * There will probably be issues when migrating non utf-8 encoded wordpress dump files (if they exist).

Other Tools
===========
 * A Gist to convert WP-Footnotes style footnotes to PHP Markdown Extra style footnotes: https://gist.github.com/1246047
