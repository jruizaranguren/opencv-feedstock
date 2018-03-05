Aim of this fork
============
This repository is a fork from https://github.com/conda-forge/opencv-feedstock

The aim is two fold:

* Allow the usage of tbb instead for multiprocessing. Multiprocessing causes problems with opencv when running on parallel as explained in the following issue.  
https://github.com/conda-forge/opencv-feedstock/issues/104#issuecomment-366571850
* Use forked version of opencv at https://github.com/jruizaranguren/opencv/tree/3.3.1-BG10-fix, that solves problems with `cypress` cameras and capture palette `V4L2_PIX_FMT_SBGGR10` and also sets `DEFAULT_V4L_BUFFERS=1`.

The opencv package has been uploaded to the following conda channel.  
https://anaconda.org/jruizaranguren/opencv

The only limitation is that intel tbb should be installed separately because there was a problem in opencv compilation. Hopefully on opencv 3.4 this problem will dissapear. Use the following command to install tbb.

```
  sudo apt-get install libtbb-dev
```

How to build
============

```
  conda-build recipe -c conda-forge
``` 

Caveats
=======

* This package has been tested only in Ubuntu 16.04.


About opencv
============

Home: http://opencv.org/

Package license: BSD 3-clause

Feedstock license: BSD 3-Clause

Summary: Computer vision and machine learning software library.



Current build status
====================

Linux: [![Circle CI](https://circleci.com/gh/conda-forge/opencv-feedstock.svg?style=shield)](https://circleci.com/gh/conda-forge/opencv-feedstock)
OSX: [![TravisCI](https://travis-ci.org/conda-forge/opencv-feedstock.svg?branch=master)](https://travis-ci.org/conda-forge/opencv-feedstock)
Windows: [![AppVeyor](https://ci.appveyor.com/api/projects/status/github/conda-forge/opencv-feedstock?svg=True)](https://ci.appveyor.com/project/conda-forge/opencv-feedstock/branch/master)

Current release info
====================
Version: [![Anaconda-Server Badge](https://anaconda.org/conda-forge/opencv/badges/version.svg)](https://anaconda.org/conda-forge/opencv)
Downloads: [![Anaconda-Server Badge](https://anaconda.org/conda-forge/opencv/badges/downloads.svg)](https://anaconda.org/conda-forge/opencv)

Installing opencv
=================

Installing `opencv` from the `conda-forge` channel can be achieved by adding `conda-forge` to your channels with:

```
conda config --add channels conda-forge
```

Once the `conda-forge` channel has been enabled, `opencv` can be installed with:

```
conda install opencv
```

It is possible to list all of the versions of `opencv` available on your platform with:

```
conda search opencv --channel conda-forge
```


About conda-forge
=================

conda-forge is a community-led conda channel of installable packages.
In order to provide high-quality builds, the process has been automated into the
conda-forge GitHub organization. The conda-forge organization contains one repository
for each of the installable packages. Such a repository is known as a *feedstock*.

A feedstock is made up of a conda recipe (the instructions on what and how to build
the package) and the necessary configurations for automatic building using freely
available continuous integration services. Thanks to the awesome service provided by
[CircleCI](https://circleci.com/), [AppVeyor](http://www.appveyor.com/)
and [TravisCI](https://travis-ci.org/) it is possible to build and upload installable
packages to the [conda-forge](https://anaconda.org/conda-forge)
[Anaconda-Cloud](http://docs.anaconda.org/) channel for Linux, Windows and OSX respectively.

To manage the continuous integration and simplify feedstock maintenance
[conda-smithy](http://github.com/conda-forge/conda-smithy) has been developed.
Using the ``conda-forge.yml`` within this repository, it is possible to re-render all of
this feedstock's supporting files (e.g. the CI configuration files) with ``conda smithy rerender``.

For more information please check the [conda-forge documentation](https://conda-forge.org/docs/).

Terminology
===========

**feedstock** - the conda recipe (raw material), supporting scripts and CI configuration.

**conda-smithy** - the tool which helps orchestrate the feedstock.
                   Its primary use is in the construction of the CI ``.yml`` files
                   and simplify the management of *many* feedstocks.

**conda-forge** - the place where the feedstock and smithy live and work to
                  produce the finished article (built conda distributions)


Updating opencv-feedstock
=========================

If you would like to improve the opencv recipe or build a new
package version, please fork this repository and submit a PR. Upon submission,
your changes will be run on the appropriate platforms to give the reviewer an
opportunity to confirm that the changes result in a successful build. Once
merged, the recipe will be re-built and uploaded automatically to the
`conda-forge` channel, whereupon the built conda packages will be available for
everybody to install and use from the `conda-forge` channel.
Note that all branches in the conda-forge/opencv-feedstock are
immediately built and any created packages are uploaded, so PRs should be based
on branches in forks and branches in the main repository should only be used to
build distinct package versions.

In order to produce a uniquely identifiable distribution:
 * If the version of a package **is not** being increased, please add or increase
   the [``build/number``](http://conda.pydata.org/docs/building/meta-yaml.html#build-number-and-string).
 * If the version of a package **is** being increased, please remember to return
   the [``build/number``](http://conda.pydata.org/docs/building/meta-yaml.html#build-number-and-string)
   back to 0.
