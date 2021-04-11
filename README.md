# Assignment 1:  Git, C, Python, and the GNU Scientific Library

The purpose of this assignment will be to guide you through setting up your laptop for this course.  This will involve installing some common software you may not already have.  
Once you have completed Part 1, you can test that your setup is working in Part 2.

## Part 1: Preparation

### In Brief

For Windows 10, you will enable Windows Subsystem for Linux, install Ubuntu on it, then in Ubuntu, you will install a C complier some other utilities.  For macOS, you will install a C complier and some other utilities.  For any operating system, you will install a recent Python 3 distrubtion.

### Details: Windows 10-Specific Stuff

1. [Enable Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/) (WSL) and update to version 2 if your specific build of Windows 10 permits it.
2. Install a Linux distribution **from the Microsoft Store** on top of WSL.  My recommendation is Ubuntu 20.04.
3. Launch your Linux WSL instance from the Start Menu; you will need to follow prompts for some one-time setup tasks.
4. At the `$` prompt, do the following:
   ```bash
   $ sudo apt install gcc git gsl libgsl-dev gdb
   ```
   Answer yes to any prompts.
5. Python options (you can do either or both):
    1. Install a python distribution inside your Ubuntu WSL instance:
       ```bash
       $ sudo apt install python3
       ```
    2. Install python natively in Windows from python.org (make sure you check the box Add Python to PATH in the install window!)
6. The baseline Python installation lacks some packages that we will use.  To add them to your Python, use the command
   ```bash
   pip install matplotlib
   ```
   You can issue this command at the WSL `$` prompt to update your Python in Ubuntu, or at a PowerShell or `cmd` prompt in Windows 10 to update your Windows 10 Python.
7. (Recommended, not required)  Install [Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/)

### Details: macOS-Specific Stuff

(disclaimer--I am not a Mac person so you might have to muddle through this)
1. Install/enable the [Terminal](https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/) app if you haven't already.
2. (Recommended) At the terminal command-line, [switch your default shell from `zsh` to `bash`]({https://www.howtogeek.com/444596/how-to-change-the-default-shell-to-bash-in-macos-catalina/).
3. Install xCode.  This should provide `gcc` (the C compiler) and `git` (revision control).
4. Install the GNU Scientific Library.  You need to either use homebrew or [compile it yourself](https://gist.github.com/TysonRayJones/af7bedcdb8dc59868c7966232b4da903).
5. Install Python from python.org.
6. Install matplotlib in Python using `pip install matplotlib` at the command line.

### Common Stuff

1. (Recommended) Install [VSCode](https://code.visualstudio.com/download).  If you don't, it is expected you prefer to work with some other text editor or integrated development enviroment.
2. Install [VMD](http://www.ks.uiuc.edu/Research/vmd).

### Configure git (One-time only commands)

1. If you have not already done so, create a public-private key pair with the `ssh-keygen` command:
   ```
   $ ssh-keygen -t rsa -b 2048
   ```
   Just use an empty passphrase and let it store the pair in the default location.  The options above are semi-standard: a 2,048-bit key pair using the RSA scheme.  `ssh-keygen` has other options for key pairs.

2. Provide your github account with your *public* key.  See instructions for this at [this link](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).

3. Now, make a nice clean directory into which you can clone all assignment and project repositories (as they are released):

   ```bash
   $ cd
   $ mkdir cheT580
   $ cd cheT580
   ```

## Part 2: The Assignment

1. Clone this repository to your local machine, and `cd` into the working directory, and launch VScode:
   ```bash
   $ git clone git@github.com:<repository-name>
   $ cd <repository-name>
   $ code .
   ```
   Here, `<repository-name>` is a custom name for your copy of the assignment repository, which you should see on the assignment page in Gitub Classroom.
2. Compile the C program `gsl_test.c`, and run it:
   ```bash
   $ gcc -o gsl_test.c -lgsl
   $ ./gsl_test
   ```
   You can do this at a standalone terminal command-line, or inside VScode.  Note that a new file has been created.  You can look at this file by opening it in VScode.  Try to match up what you see in the file with the contents of the C program.
3. Modify `gsl_test.c` to generate the additional required output, recompile, and run.
4. Compile the program `hhd.c`, and run it:
   ```bash
   $ gcc -o hhd hhd.c -lm
   $ ./hhd 10
   ```
   The `10` command-line argument is a number of "generations" of a fractal curve called the Harter-Heighway Dragon that `hhd.c` will generate.  Note the name of the output file this execution generates.
5. Run the python script `plot_dragon.py` according to its instructions.  Note the name of the image file generated.  You can also view this image from VScode, or as a photo.
6. **Submit** your results by adding, committing, and pushing:
   ```
   $ git add .
   $ git commit -m "My Assignment 1 Results"
   $ git push
   ```
   You can add, commit, and push as many times as you like up to the deadline.

Some things to keep in mind:

* If you are using VScode, you should be seeing prompts to install certain "extensions"; I recommend you install any extensions suggested that are provided by Microsoft; this will probably amount to the C/C++ extension and the Python extension.
* Note any error messages generated by any of these commands; I recommend keeping a log of them in text file that you can show me.  Our primary objective with this assignment is to be sure your laptop is minimally functional for this course. 
* The Ubuntu installation on top of WSL is a fully-functional Linux command-line.  All the contents of your `C:\>` drive are visible from within Ubuntu at the path `/mnt/c/` (other drive letters are similarly mapped).  I recommend that you keep your work in this course **inside** your Linux installation filesystem, `/home/<your-username>/`.  Should you ever need to see anything inside Linux from Windows, you can copy it out to `/mnt/c/Users/<your-username>/` or some subfolder of that.