#QIIME Tutorial (CENTA 10th June)

##Getting started with VMs

You will be walked through this with Marius but basically you need to:

* Login to http://warwick.climb.ac.uk with your username and password

* Launch a new *instance* from the *CENTA-final* image select *public* network and *climb.medium* 
configuration

* Once your instance is booted note the IP address assume it is www.xxx.yyy.zzz

* Then login to instance from MacBook provided

```
ssh ubuntu@137.205.68.252
```

## Qiime tutorial

This is a slightly edited version of the standard [Illumina QIIME overview](http://nbviewer.jupyter.org/github/biocore/qiime/blob/1.9.1/examples/ipynb/illumina_overview_tutorial.ipynb)
tutorial and all credit belongs to the original authors:

We begin by moving into our working directory which should have the tutorial data available already:

```
cd Projects
```

Projects is a special directory in that a web server is installed there allowing generated 
html results to be viewed on our laptops, through a browser.

Now 

```

