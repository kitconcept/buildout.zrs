ZEO REPLICATION EXAMPLE
=======================

Set up a master ZEO
-------------------

master.cfg::

  [zeo]
  recipe = plone.recipe.zeoserver[zrs]
  eggs =
    Plone
    plone.recipe.zeoserver[zrs]
  zeo-address = 8000
  replicate-to = localhost:9000

Start the instance and 'var/log/zeo.log' should include::

  PrimaryFactory starting on 8000
  2013-11-26T08:19:38 Starting factory <zc.zrs.primary.PrimaryFactory instance at 0x999d42c>


Set up a slave ZEO
------------------

slave.cfg::

  [zeo]
  recipe = plone.recipe.zeoserver[zrs]
  eggs =
    Plone
    plone.recipe.zeoserver[zrs]
  zeo-address = 8000
  replicate-to = localhost:9000

  [instance]
  recipe = plone.recipe.zope2instance
  read-only = True

var/log/zeo.log::

  2013-11-26T08:23:14 IPv4Address(TCP, '127.0.0.1', 9000): Connected


Sync Databases
--------------

If you have an existing Database, make sure you copied over 'var/filestorage' and 'var/blobstorage' from master to slave.


Further reading
---------------

* https://pypi.python.org/pypi/zc.zrs/2.4.4
* https://pypi.python.org/pypi/plone.recipe.zeoserver
* http://stackoverflow.com/questions/18742513/plone-switching-to-zrs-using-plone-recipe-zeoserver-on-plone-4-3-1
* https://github.com/codesyntax/buildout.zrsexample/blob/master/buildout.cfg
