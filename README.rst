https://pypi.python.org/pypi/zc.zrs/2.4.4
https://pypi.python.org/pypi/plone.recipe.zeoserver
http://stackoverflow.com/questions/18742513/plone-switching-to-zrs-using-plone-recipe-zeoserver-on-plone-4-3-1


1) Set up two zeo instances (master and slave)
2) Set up the 'replicate-to' setting of the master zeo instance to the slave
3) Set up the 'replicate-from' setting of the slave zeo instance to the master
4) Set up the slave instances to 'read-only'
