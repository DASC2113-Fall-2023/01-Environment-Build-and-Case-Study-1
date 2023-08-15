# Scientific Python Setup for MacOS

- Python is open, so we have many choices, even in simply setting it up.

- We've made choices here that we hope are best for Data Science work, but nothing here is _the right way_ to do it.

- Find all the python installations in your PATH. Your PATH determines the order of directories MacOS searches for 
   programs your run. To see all the python installations in your current PATH, in a `Terminal` type 
  
        echo $PATH
        which -a python
        which -a python3 

- OPTIONAL Uninstall existing VSCode installation and other versions of Python.

## Install Python

- There are many ways to install Python beyond the official installer. There
  are also many ways to get all the extra libraries you want that don't come
  with Python itself.

- Python.org hosts the official installers. The Python Package Index (PyPI)
  is the central source of extra libraries. 

- Python.org installs python in `/Library/Frameworks/Python.framework` 
  (you likely have several versions here)

- You might also have a versions in `/Users/jcothren/Library/Python` 

- The first location is used if you chose install for all users. The second 
  if it was only for your account.

- PyPI is a bit archaic, so there are various projects that provide
  essentially a curated copy of it. We'll use one of those: Anaconda. Actually,
  we'll use the condensed version: Miniconda3. The 3, of course, is for Python3.

1. Go to the [miniconda][] page, download the Miniconda3 MaxOSX 64-bit pkg
   and run it. Choose the `Install only for me option`. The other default options 
   are good.

2. Open a `Terminal`. This will start a terminal with the `base` environment
   installed. Note how prompt has been modified with `(base_)` preceding your
   prompt. The `bash` (that's your shell language) command that does that is in
   your `/Users/username/.bash_profile` file. This is a file that is run
   everytime you open a new `Terminal` (even when opened in VSCode).
   - You can look at this file by typing `more /Users/username/.bash_profile`.

3. Look _under the hood_ and find your python execution (that name, no extension)
   file using the command 
   
        which -a python3
   
   (there should be a version in `\\User\username\opt\miniconda3\` or `\\User\username\opt\bin\miniconda3`). 

3. Run `conda -V` to see if it installed correctly. Then run `python -V` and
   see what version of Python is running. (should be `3.9.7`). Just in case, 
   run `conda update python` to get the lastest. Then run `pip -V` to see that 
   `pip` is also installed. NOTE: When we install packages for class, we'll use `conda` exclusively.

4. Type `conda list` to see all the installed packages ( `\Users\jcothren\opt\miniconda3\pkgs`)

5. Geopandas is useful as a programming library, and as a high-level package
   that pulls in all the gis and most datas science software you need. It has 
   [specific advice][] on creating conda environments.

   In the `Terminal` and type:

        conda create -n geoenv
        conda activate geoenv
        conda config --env --add channels conda-forge
        conda config --env --set channel_priority strict
        conda install geopandas scipy jupyter matplotlib pyyaml flake8

   It will take a minute to think, then hit Y to proceed. Documentation on [channels][4].

   NOTE: You might not want to start base:conda every time you open a terminal. You 
   can turn off this behavior by typing
   
        conda config --set auto_activate_base False
   
   You can activate base at any time with

        conda activate base
   
   IMPORTATE: Pay attention to which environment you're in. You'll default to base and will
   need to activate your class environment in both the terminal and in VSCode.

6. In the `Terminal` run `python` and try `import geopandas`. Also run `ipython`, just to see
   what it is.


[miniconda]: https://docs.conda.io/en/latest/miniconda.html
[specific advice]: https://geopandas.org/getting_started/install.html#using-the-conda-forge-channel
[vscode]: https//:https://code.visualstudio.com/Download

## Install a nice IDE: Visual Studio Code (VSCode)

We're going to install VSCode. It's generally regarded as one of the best
IDEs for general Python programming. It can, however, be a little intimidating at first glance. It
is important to focus on only a few features at first. Keep it simple.

1. Download and install [vscode][1].

2. Unlike most applications, the VSCode App will be saved in whatever directory you told
   it to download to. Before you start it, drag the _Visual Studio Code_ app to your 
   `/Applications` directory. 

3. Run Visual Studio Code and the launch sceen will open. We want to make sure vscode recognizes
   our conda environment and recongnizes any recent folders we've worked in. Click `Open...` and
   choose the directory where you keep all our class files (.ipynb, .py, .csv, ...) and 
   git repositories.

4. You should see the file and directory structure in the panel on the left. Look to the upper right 
   in the menu bar. You should see Python 3.9.5 64-bit ('base':conda) as the current python interpretor.
   Click on this and you'll see a list of the available interpretors available, indcluding the 
   Python 3.9.7 64-bit ('geoenv':conda) interpretor. Note that base and geoenv have different 
   versions of python and will have different packages.

   NOTE: If you create a new environment with VSCode open it will not be recognized in the current open
   Windows. Opening a new Window will rerun the search through PATH for available interpretors in that
   and future windows.

There alternatives to VSCode, like PyCharm which is a very different
animal and very popular. [This post][2] compares some of the IDEs you can use
for scientific Python.

[1]: https://code.visualstudio.com/download
[2]: https://medium.com/@rasmusgs/python-for-matlab-users-part-3-choosing-an-ide-af45b427d183
[4]: https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html


## Git and GitHub

### Install Git

If you already have git installed (or think you do) start with step 2. It `git` is not installed it will prompt you to install using the CLI option described in step 1. You can proceed or decline and use the GUI installer.

1.   Download and run git [git-download][]. Use either the command line interface (CLI) in `Terminal` or the GUI-based installer. I recommend the CLI method but it's up to you. Use all the default options. Note that installing the XCode Command Tools will take some time. Be patient. Note that you also have the option of installing via MacPorts and Homebrew. Instructions at [git-scm][]

2. Open the MacOS `Terminal` and type

       git --version

3. Do some basic configuration of git by typing:

       git config --global user.name "John Doe"
       git config --global user.email johndoe@example.com
       git config --global init.defaultBranch main

[git-download]: [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git]
[git-scm]: [https://git-scm.com/install-guide/macos]

### Fork or Clone a Project

1. If you've got a project open in PyCharm, `File` menu -> `Close Project`.
   You should see a window titled `Welcome to PyCharm`.

2. Go to a project page in gitlab, for example
   https://github.com/dasc2113/course-intro-and-setup

3. Click `Clone`, then click the Copy URL button next to `Clone with SSH`.

4. Back on the PyCharm Welcome screen, click `Get from VCS`.

5. Paste in the URL you copied from gitlab.

6. Go to the `View` menu and select `Scientific Mode` to get the same layout
   you saw before.


## Additional Resources for Python Learning

Two to five days's worth of self-instruction: <http://scipy-lectures.org/>

From the Enthought folks who wrote that white paper I emailed earlier, a
one-hour webinar on Python for MATLAB Users:
<https://www.youtube.com/watch?v=YkCegjtoHFQ>

And an updated version of that same whitepaper:
<https://www.enthought.com/wp-content/uploads/2019/08/Enthought-MATLAB-to-Python-White-Paper_.pdf>
