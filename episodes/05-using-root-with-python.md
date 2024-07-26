---
title: "Using ROOT with python"
teaching: 5
exercises: 0
---

:::::::::::::: questions

- Can I call ROOT from python?

::::::::::::::

:::::::::::::: objectives

- Find resources for PyROOT
- Find resources for Scikit-HEP

::::::::::::::


## PyROOT

The PyROOT project started with Wim Lavrijsen in the late `00s and became very popular, 
paralleling the rise of more general python tools within the community. Python has become the primary analysis language for the majority of HEP experimentalists. It has a
rich ecosystem that is constantly evolving. This is a good thing because it means that improvements
and new tools are always being developed, but it can sometimes be a challenge to keep up with the 
latest and greatest projects! :)

If you want to learn how to use PyROOT, you can go through some individual examples
[here](https://root.cern.ch/doc/master/group__tutorial__pyroot.html), or a more guided tutorial
[here](https://root.cern/manual/python/).

Feel free to challenge yourself to rewrite the previous C++ code using PyROOT! 

## Scikit-HEP libraries

Over the past several years, an effort has developed to provide more python tools that can interface with CMS ROOT file formats as well as typical scientific python tools used widely beyond particle physics.
We will use several of the [Scikit-HEP](https://scikit-hep.org/) libraries to analyze NanoAOD: `uproot`, `awkward`, and `vector`. As CMS datasets grow larger, we increasingly rely on tools for array-based 
data processing in python, and the scikit-HEP tools are very important for that task. 

You can check out a tutorial for many of their tools [here](https://hsf-training.github.io/hsf-training-scikit-hep-webpage/). 

## Using the Python docker container

The tools in the Python docker container will allow you to can easily open
and analyze ROOT files. This is useful for when you make use of the CMS open data tools to skim 
some subset of the open data and then copy it to your local laptop, desktop, or perhaps an 
HPC cluster at your home institution. 

If you completed the [Docker pre-exercises](https://cms-opendata-workshop.github.io/workshopwhepp-lesson-docker/) 
you should already have worked through 
[this episode](https://cms-opendata-workshop.github.io/workshopwhepp-lesson-docker/03-docker-for-cms-opendata/index.html), under **Download the docker images for ROOT and python tools and start container**, and you will have

- a working directory `cms_open_data_python` on your local computer
- a docker container with name `my_python` created with the working directory `cms_open_data_python` mounted into the `/code` directory of the container.

Start your python container with

```bash
docker start -i my_python
```

In the container, you will be in the `/code` directory and it shares the files with your local `cms_open_data_python` directory.

:::::::::::: callout

## If you're using apptainer:

Whenever you see a `docker start` instruction, replace it with `apptainer shell` to open either the ROOT or Python container image.
The specific commands in this pre-exercise and during the live workshop will be given for docker, since that is the most common application.
As a general rule, editing of files will be done in the standard terminal (the containers do not have all text editors!) or via the jupyter-lab interface, and then commands will be executed inside the container shell. If you see `Singularity>` on your command line, you are ready to run a ROOT or python script.

:::::::::::::

If you want to test out the installation, from within Docker you can launch and 
interactive python session by typing `python` (in Docker) and then trying

```python
import uproot
import awkward as ak
```

If you don't get any errors then congratulations! You have a working environment and you are ready to
perform some HEP analysis with your new python environment!

:::::::::::::: keypoints

- PyROOT is a complete interface to the ROOT libraries
- Scikit-HEP provides tools to interface between ROOT and global scientific python tools
- We will use `uproot`, `awkward`, and `vector` in our NanoAOD analysis

::::::::::::::
