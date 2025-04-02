# The Python Beginner's First Project Setup (working title)

## Intro
*Simple Script Paradise Island.*

Every Python programmer starts out their Python journey here - writing simple one-file scripts written purely in Python,
using only the packages present in the Python Standard Library. 

In Paradise Island, everything is perfect. The weather is a 
balmy 20°C/77°F with clear skies all day every day. You sip your pina-colada upon the beach, with nary a worry in your 
mind, enjoying the occasional gentle sea breeze and a dip in the ocean.

Some stay here longer than others. Those learning programming for the first time will enjoy a longer stay than 
those who come learning Python as an additional language.

But sooner or later, everyone must leave.

Somewhere out there in the distance is the *Realm of Projects*. A land several hundreds of times larger than Simple Script 
Paradise; this is where structured project development happens. Multi-file projects, multi-developer projects, 
and projects with external dependencies - code written by others, for usage in Python programs, 
not present in a standard Python installation.

If you want to write any project that has any value attached to it, you'll be relying on external 
dependencies. And so, one day, you'll need to embark upon the trip, as many have done before you.

There's only one problem - that which lies between Paradise Island and the Realm of Projects.

### The Gulf of Abject Misery and Treachery

A murky, shark infested sea lies between the two lands. Broken imports, broken tools, broken builds, even broken 
operating systems - all these prizes and more await you should you perform the crossing in the wrong way. 

The problem is, to build a boat suitable for the crossing, and not one based on driftwood, duct tape and broken dreams - 
much must be understood. 

* You need to understand imports, how Python thinks about imports, and sys.path - the list of paths that Python looks at
when trying to resolve imports.
* You need to understand pyproject.toml - the modern approach to describing a Python project, and how it is used to build 
a project.
* You should understand the src project layout - the best way to structure your project such that everything *just works*.
* You must understand pip - the default Python dependency resolver and installer - the correct way to use it to install 
* dependencies, and how it can be used to generate a list of dependencies currently installed
* You MUST understand virtual environments and the venv module - the way in which dependencies for a project are isolated
(and just why this is so important to do each and every time)
* And, you should understand editable project installs - how to place your project on the sys.path such that
your intra-project imports *just work*.

You may think this is a lot to learn for project set up. Know that this is just the minimum, and that depending on the
project you decide to build, you may need to set up far more than this. Unfortunately, it is impossible to give bespoke
instructions to everyone, simply because Python is so popular and so widely used in a bunch of different disciplines that
one could not hope to cover them all. 

However, the above is sufficient for a "simple" Python project a beginner may start with.  

### A UV Ray of Hope on the Horizon

In the darkness shines a single ray of UV light. 

The uv dependency manager, written by astral, has quickly emerged as a front-runner of the Python dependency manager 
scene, despite first being released only just in Feb 2024. It supplants pip and venv - but can do so much more, replacing 
several other tools that were released to do various things in the project management space (pip tools, pipx, pyenv and more).
As the last part of this guide, we will go over uv and demonstrate how and why it should be used for project setup and 
management.


## Prerequisites

### Knowledge
Strictly speaking, there are no knowledge prerequisites for this guide. However, since this is aimed at people who want to be able
to code more complex Python projects, there are things you should learn first.

#### Terminal usage
Much project set-up occurs via the terminal. You don't need to know much about the terminal for this guide beforehand, 
as all commands will be explained; but a little experience beforehand (e.g. knowing how to launch it, how to change directories, how to see all files in a directory) will help.

#### Python

This guide is aimed at Python beginners who are comfortable in coding 
simple single-file scripts that have no dependencies. 

If you aren't sure whether you meet that criteria, then ask yourself the 
following - can you write a simple terminal calculator app using Python? 

If you can't, you should focus on learning enough Python first before continuing - any good Python learning resource will do.

#### Git

The other thing you need to know is version control. 99.9% of the time, this means Git. 

If you want to code anything other than the simplest of simple projects, then you need to know version control - there are no exceptions to the rule. 

You should
know to set up a Git repo, how to clone an existing GitHub repo, checking-out branches, committing files, 
pushing changes to GitHub, fetching updates from a GitHub repo and pulling/merging changes from a GitHub project into your local project.

If any of those seem unfamiliar, please seek out and follow any good Git learning resource before proceeding.

## Installing Python

If you are interested in this guide, you probably already have Python installed. Even so, I would recommend you install Python through uv. There are particular reasons why we want to install Python this way - later sections will cover this in more detail, but 
it is sufficient to know the following for now:

* If you are on macOS and Linux, you may currently be using the Python that came with your OS - the system Python. However, you can brick your OS if you mess around with the system Python. In general, you should
refrain from using it as it exists to run programs for your OS, not to run programs you develop 
yourself. Installing a separate version of Python is recommended, and doing so through uv is considered safe.
* For certain Linux distributions (and definitely Ubuntu, the most popular flavour of desktop Linux), the system version of Python (which, as mentioned above, is not one you should use
anyway) does not contain pip or venv. We will be using these tools in this article, so we will need a version of Python
that has them installed.

Install astral's uv following the link here: https://docs.astral.sh/uv/getting-started/installation/ . You can either
install it using a terminal command or by using your package manager of choice. 

Open the terminal in your OS and run the `uv` command to verify that it works.

From there, install Python with the following commands: 

```
$ uv tool update-shell
$ uv python install --default --preview
```

Run the `python` command and verify Python is now installed:

```
$ python
Python 3.13.2 (main, Mar 17 2025, 21:02:54) [Clang 20.1.0 ] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

## Editor
The most popular editors for Python are PyCharm
and Visual Studio Code. That said, for this guide, use a simpler editor to follow along (Notepad/Notepad++ on Windows, TextEdit on plain text mode on macOS, Gedit/Kate on Linux). The later part of this guide will show you how to set up PyCharm and Visual Studio Code with uv.

## sys.path - how Python understands imports





