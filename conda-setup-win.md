# Scientific Python Setup for Windows

- Python is open, so we have many choices, even in simply setting it up.

- We've made choices here that we hope are best for Data Science work, but nothing here is _the right way_ to do it.

- Python 2 vs. Python 3

- Check existing version 'python --version' in your terminal/cmd

- Uninstall existing VSCode installation and other versions of Python.

- Restart your PC, once uninstallation of existing versions of Python is done. 

## Install Python

- There are many ways to install Python beyond the official installer. There
  are also many ways to get all the extra libraries you want that don't come
  with Python itself.

- Python.org hosts the official installers. The Python Package Index (PyPI)
  is the central source of extra libraries.

- PyPI is a bit anarchic, so there are various projects that provide
  essentially a curated copy of it. We'll use one of those: Anaconda.

1. Go to the [python](https://www.python.org/downloads/) page, download the latest 
   version for Windows (`Download Python 3.9.7`), and run it. In the `Install Python 3.9.7`
   check the `Add python 3.9.7 to PATH`. The other default options are good. 
   In Windows search type `cmd`, run `Command Prompt`, and type `python -V` to see the python version installed.

1. Go to the [miniconda][] page, download the Python 3.X version for 64-bit
   windows, and run it. In the `Installation Type` check `Just for me` -- you can also cehck `All Users`. In the `Advanced Installation Options` check the 
   `Add Anaconda to my PATH environment variable`. The other default options
   are good.

2. Open a `Anaconda Prompt`. This will start a terminal with the `base` package 
   installed.

3. Look _under the hood_ and find python.exe file using the command 
   `where.exe python` (there should be a version in '\\User\Username\Miniconda\`) 
   and where packages are installed. 

3. Run `conda -V` to see if it installed correctly. If your conda is version 3.X, then update the conda using `conda update conda`. Then run `python -V` and see what version of Python is running. (should be `3.9.7`). Just in case, 
   run `conda update python` to get the lastest. Then run `pip -V` to see that 
   `pip` is also installed.

4. Install data science packages. Still in the `Anaconda Prompt` type `conda install 
   numpy scipy matplotlip seaborn pandas geopandas jupyter ipython`

5. Type `conda list` to see all the installed packages.   

6. FOR INFORMATION ONLY Geopandas is useful as programming library, and as a high-level package
   that pulls in all the gis software you need. It has [specific advice][] on
   creating conda environments.

   Run the "Anaconda Prompt" and type:

        conda create -n geoenv
        (conda create --name geoenv)
        conda activate geoenv
        conda config --env --add channels conda-forge
        conda config --env --set channel_priority strict
        conda install geopandas scipy jupyter matplotlib pyyaml flake8

   It will take a minute to think, then hit Y to proceed.

7. In the `Anaconda Prompt` run `python` and try `import geopandas`. Also run `ipython`, just to see
   what it is.


[miniconda]: https://docs.conda.io/en/latest/miniconda.html
[specific advice]: https://geopandas.org/getting_started/install.html#using-the-conda-forge-channel
[vscode]: https//:https://code.visualstudio.com/Download

## Install a nice IDE

We're going to install VSCode. It's generally regarded as one of the best
IDEs for general Python programming. 

1. Download and install [vscode][1].

2. Run vscode and the launch sceen will open. We want to make sure vscode knows
   about our conda environment.

3. Choose `Python Interpreter` on the left. If you don't see the option, close VScode and relaunch VSCode.

4. There's a pulldown menu labeled `Python Interpreter:` with `<no interpreter>`
   inside it. Click the gear button to the right, then click `Add...`

5. Select `Conda Environment` on the left, then the `Existing Environment` radio
   button. It may already have filled in the correct path; for me, that's:

        C:\Users\seth\miniconda3\envs\geoenv\python.exe
   
   Note the `geoenv` matches the environment we created. If the path isn't there,
   use the `...` button and add it.

6. Check `Make available to all projects`, then `OK`. It will think for a minute.

7. Hit `Apply` then `OK` in the "Settings for New Projects" window.

8. Restart VSCode.

To create a new project:

1. Select `New Project` on the launch screen.

2. Select `Scientific` on the left side.

3. Expand the `Python Interpreter` section on the right.

4. Choose `Previously Configured Interpreter`; you should see the environment you picked
   earlier. In my case, "Python 3.9 (geoenv)".

5. In the `Location` box at the top, change the folder name to whatever works
   for you. This is where the code you write will be saved.

6. Take a look at the script window, the interactive interpreter, the
   magic `%run` command, and the data view.

PyCharm has extensive documentation, [this][2] is the section focusing on
Scientific Mode.

An alternative to Visual Studio Code is PyCharm which is a very different
animal and very popular. [This post][3] compares some of the IDEs you can use
for scientific Python.

[1]: https://code.visualstudio.com/download
[2]: https://www.jetbrains.com/help/pycharm/matplotlib-support.html#data
[3]: https://medium.com/@rasmusgs/python-for-matlab-users-part-3-choosing-an-ide-af45b427d183


## Git

### Install Git

1. Download and run the [git installer][4].

2. Use all the default options.

3. Run the Anaconda Powershell Prompt from the Start Menu again, and verify
   that git is installed by typing:

       git --version

4. Do some basic configuration of git by typing:

       git config --global user.name "John Doe"
       git config --global user.email johndoe@example.com
       git config --global init.defaultBranch main

[4]: https://git-scm.com/download/win


## Additional Resources for Python Learning

Two to five days's worth of self-instruction: <http://scipy-lectures.org/>

From the Enthought folks who wrote that white paper I emailed earlier, a
one-hour webinar on Python for MATLAB Users:
<https://www.youtube.com/watch?v=YkCegjtoHFQ>

And an updated version of that same whitepaper:
<https://www.enthought.com/wp-content/uploads/2019/08/Enthought-MATLAB-to-Python-White-Paper_.pdf>
