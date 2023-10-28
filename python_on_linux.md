# How to Install Python 3.12 in Ubuntu 22.04 | 20.04 | 23.04

*Last updated: October 3, 2023*

For developers who want to prepare their project for the latest Python releases, here’s how to install Python 3.12 in all current Ubuntu releases.

Python 3.12 finally goes stable. It features more flexible f-string parsing, Per-Interpreter GIL, new type annotation syntax for generic classes, support for the Linux perf profiler, and many performance improvements, but removed the distutils package and wstr from Unicode. See more about Python 3.12.

# How to Install Python 3.12
Python is easy to install in Ubuntu by either using the popular Deadsnakes PPA or building from the source. Choose either one that you prefer.

## Option 1: Install Python 3.12 from PPA
For Ubuntu 22.04, Ubuntu 20.04, and their derivatives such as Linux Mint 21, the Deadsnakes PPA has made the packages for all supported CPU architecture types: amd64, arm64/armhf, ppc64el, and s390x.

1. First, press Ctrl+Alt+T on keyboard to open terminal. Then paste the command below and hit run to add PPA:

<code>sudo add-apt-repository ppa:deadsnakes/ppa</code>

Type user password (no asterisk feedback) when it asks and hit Enter to continue.

2. Ubuntu 20.04+ automatically refresh package cache while adding PPA. However, Linux Mint user may need to do this job manually by running command:

<code>sudo apt update</code>

3. Finally, run command to install Python 3.12:

<code>sudo apt install python3.12</code>

## Option 2: Compile and install Python 3.12 from source

Don’t trust third-party repositories or you’re running Ubuntu 23.04 or Ubuntu 18.04? It’s easy to build Python from the source tarball.

1. First download the source tarball from its ftp download page:

[Python FTP Download Page](#)

2. Then open ‘Downloads’ folder, extract the source tarball, finally right-click on source folder and select “Open in Terminal”.

3. When terminal opens, run the commands below one by one to configure and build Python:

<code>./configure --enable-optimizations</code>

<code>sudo make -j4 && sudo make altinstall</code>

NOTE: You have to first install all build dependency libraries before running last 2 commands. See this tutorial for details.

### Verify:

Once installed Python 3.12, verify by running command:

<code>python3.12 --version && pip3.12 --version</code>

## Set Python 3.12 as default

It’s NOT recommended to set non-preinstalled Python package as default for Python3, since it will break some core applications.

However, you may try to set python3.12 as python by running the commands below one by one:

First, run command to find out where Python 3.12 executable is installed to:
whereis python3.12
It’s either /usr/bin/python3.12 or /usr/local/bin/python3.12.

Then, add Python 3.12 as an alternative link to python (replace /usr/local/bin/python3.12 according last command output).

<code>sudo update-alternatives --install /usr/bin/python python /usr/local/bin/python3.12 1</code>

Finally, run command to set default for /usr/bin/python executable if more then one available:

<code>sudo update-alternatives --config python</code>

# Uninstall Python 3.12:
If you installed Python 3.12 using the PPA repository, simply open terminal and run command to remove it:

<code>sudo apt remove --autoremove python3.12</code>

For the PPA, run command to remove it:

<code>sudo add-apt-repository --remove ppa:deadsnakes/ppa</code>

If you built the Python 3.12 from source tarball, then there’s no uninstaller script to automate the job.

However, you may manually remove the installed files by running commands:

<code>cd /usr/local/bin && sudo rm python3.12* pip3.12 idle3.12 pydoc3.12 2to3-3.12</code>

<code>cd /usr/local/lib && sudo rm -R python3.12 pkgconfig libpython3.12.a</code>