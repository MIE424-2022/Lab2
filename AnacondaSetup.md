# Getting Anaconda Python set up and installed

## 1. Downloading the installer

### macOS
First off, we need to download the script which will be used to install Anaconda (Miniconda). Download [this file](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh) and save it in your Downloads folder, either using your web browser or by entering the command `curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh -o ~/Downloads/Miniconda3-latest-MacOSX-x86_64.sh` into your terminal.

### Windows

Unlike with macOS, we need to use a graphical installer to set up Anaconda on Windows. You can download that [here](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe).

## Linux

If you are using Linux, please let me know and we can go through the procedure depending on if you're using Intel or IBM.

## 2. Installation

### macOS

Open the Terminal application on your mac and navigate to the downloads folder like so: `cd Downloads` (`cd` stands for change directory, and is the command for navigating between folders in almost every contemporary operating system.) From here, you can confirm that the file has been downloaded correctly by entering the command `ls Miniconda3-latest-MacOSX-x86_64.sh`. If you see `No such file or directory` then you have either downloaded the file to a different directory, not downloaded the correct file, or named it differently when downloading.

Now, to install, enter the command `bash Miniconda3-latest-MacOSX-x86_64.sh` which will tell your mac to run the file as an executable (note: for long file names like this one, you can enter part of the name and then hit the tab key for the terminal to autocomplete). You will have to agree to the terms of service, and answer some configuration options, all of which you can leave at the default setting. The installation itself can take quite some time, so be patient. Once it's complete, the installer will ask you whether you want to "add anaconda to .bashrc" - I highly recommend you enter 'yes' here unless you have a specific reason to use your existing Python installation. If you are using another shell (such as zsh), I recommend you add anaconda to your .zshrc file as well.

Once the installation is complete, you need to quit and then re-open the Terminal application. Upon doing so, verify that Anaconda installed correctly by typing `python` into the terminal. You should see a message like this one: 

```
Python 3.9.5 (default, Sep  4 2020, 02:22:02) 
[Clang 10.0.0 ] :: Anaconda, Inc. on darwin
Type "help", "copyright", "credits" or "license" for more information.
```

The critical part is to verify that you see the `Anaconda, Inc.` message here - that confirms you are now using Anaconda Python.

### Windows

On Windows, open up the installer once it has been downloaded and work your way through the installation screens. Leave every setting at its default. Installation can take quite some time.

Once the installer is finished, verify that installation has completed by looking for a program in your start menu called `Anaconda Prompt`. This is what we will be using for future command line instructions, rather than the standard Windows command prompt.

### Problems?

If you have any problems up to this point, it's worth checking out the official installation instructions - [Windows](https://docs.anaconda.com/anaconda/install/windows/), [macOS](https://docs.anaconda.com/anaconda/install/mac-os/). However note that these instructions diverge slightly from what we have set out here.

## 3. Setting up a Virtual Environment

Virtual environments are a powerful tool which allows us to maintain multiple distinct Python installations. This is extremely useful when you are working on multiple Python projects at once - instead of having one messy installation with every package imagineable downloaded, virtual environments ensure that each project has its own tidy playground with only the tools it requires.

To set up your first virtual environment, open the Terminal on macOS or the Anaconda Prompt on Windows. We can then create a new virtual environment with the following command: 

```conda create --name MIE424 ```

As you might expect, the `--name` parameter tells conda that the next phrase should be the name of this virtual environment.

Conda may install some packages here, which it will ask you to confirm before doing so. Once the setup is done, you can activate the conda environment you just created by typing `conda activate MIE424` on macOS, or simply `activate MIE424` on Windows. In your prompt, you should now see the name of the enviroment in brackets before the prompt line, like so:

```
(MIE424) ➜  ~
```

This confirms that we are now in the enviroment we just created, and that anything we install into Python here will stay within this sandbox. Next, let's install some basic tools:

`conda install numpy pandas matplotlib seaborn scikit-learn`
`conda install -c conda-forge jupyterlab`


You can enumerate as many package names as you like after the `install` keyword and conda will install them all at once. Again, it may ask for your confirmation before installing any packages you don't already have.


If you have made it to here, congratulations! Your Anaconda environment is all set up, as well as your virtual environment for the first lab. You can `deactivate` your environment at any time by using the command `conda deactivate` on macOS, or simply `deactivate` on Windows.

## 4. Setting up Git

If you are using a Mac or a Linux computer, then git will already be installed. If you are using a Windows, you must install git yourself by downloading this [file](https://github.com/git-for-windows/git/releases/download/v2.34.1.windows.1/Git-2.34.1-64-bit.exe). 

Once git is installed, the next thing we want to do is set up an ssh key to easily access all of the repositories that we have access to without needing to put your credentials in every time. To do this, open up terminal (Unix based) or Anaconda prompt (Windows), and type `ssh-keygen`. Click enter on all the default options and an ssh public and private key will be made in the .ssh folder in your home directory. Head to this folder (again by using the cd command) and then display your public key by using either `cat id_rsa.pub` on a Unix based system or `more id_rsa.pub` on a Windows. Copy this public key and log onto your github in a browser. In your settings, you should see a tab for SSH and GPG keys. Add a new SSH key and paste your public key. You could now clone repositories using ssh instead of https!

To clone a repository, type `git clone {ssh repo link}` where {ssh repo link} is the link you get when you go to a repository, click on the green code button and select the ssh tab.
