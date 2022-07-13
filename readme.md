
# Table of Contents  
- Using CoreMS with Docker Compose:     
  - [CoreMS Jupyter Notebook Docker Image](#using-corems-docker-image)
- Manual Installation  
  - [MAC](#mac-installation-instructions)  
  - [Windows](#windows-installation-instructions)  


# Using CoreMS Docker Image

This option is the easiest way to get a functional CoreMS, and Jupyter notebook working locally and uses docker-compose to set up the docker container, volumes, database, and virtual networks. If you choose this option you don't need to follow the manual installtion session. 

- A custom python distribution with CoreMS and all dependencies installed
- A Jupyter notebook server with workflow example, and test data
- A PostgreSQL database for the molecular formulae library creation and search

The first step is to install docker. If you don't have docker installed yet, the easiest way is to [install docker for desktop](https://www.docker.com/products/docker-desktop/)

1. Copy your raw data into the day3-emsl-summerschool-2022/data/ directory before starting the services or : 

    - modify the volume path in the docker-compose.yml file. 
    
        - locate the volumes on docker-compose.yml (line 19):

        ```
        volumes:
        - ./data:/home/CoreMS/data
        ```
        - change ./data to your data directory path  

2. Start the services using docker-compose: 
    
    - save the file and then call:
    
    ```bash
    docker-compose up
    ```
3. On the terminal logs, find the Jupyter Notebook URL and copy and paste into your browser:  

    ```
    corems | [I 05:41:37.790 NotebookApp]  or http://127.0.0.1:8888/?token=826ba2d4b2324f03441c189ddf4d1c84e365c39fb3377dd4

    ```
4. Open the Summer School CoreMS Tutorial notebook, and you are ready to go. 
  
# MAC Installation Instructions

1. Install Python 3.9.13 following this tutorial:
  https://www.chrisjmendez.com/2017/08/03/installing-multiple-versions-of-python-on-your-mac-using-homebrew/  
  By the end of the tutorial, if you have not yet, set python 3.9.13 as the global option.  
  If you are using Z shell, make sure to add the python path to your zprofile:  
    ```
    $ echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
    ```  
2. Install git using brew

    ```
    $ brew install git
    ```
3. Install Commandline tools and GCC compilers:
    ```
    $ xcode-select –install
    $ brew install gcc
    ```
    Find the GCC version. 
    ```
    $ cd usr/local/bin
    $ find gcc*  
    gcc-11  
    gcc-ar-11  
    gcc-nm-11  
    gcc-ranlib-11  
    ```
    In this case, the version is 11. So, replace the label {version} in the next step, and the command will be: "ls -s gcc-11 gcc"

    ```
    $ ln -s g++-{version} g++ 
    $ ln -s gcc-{version} gcc

    ```
    call gcc --version to check everything is working, and it should output something like:

    ```
    $ gcc --version
    gcc (Homebrew GCC 11.3.0_2) 11.3.0
    Copyright (C) 2021 Free Software Foundation, Inc.
    This is free software; see the source for copying conditions. There is NO
    warranty, not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
    ```

4. Install Mono and DotNet. This step is needed to install Python Net, which is used to read Thermo raw files. 
    ```
    $ brew install pkg-config
    $ brew install mono-mdk
    $ brew install mono
    $ brew install dotnet
    ```
    At this point, you should have all the compilers and software framework needed to install corems

5. Go ahead and use git to clone the Day 3 tutorial repository into a location of your choice. 
    ```
    $ git clone https://github.com/EMSL-Computing/Day3-EMSL-SummerSchool-2022
    ```  
6. After the cloning process, go to the newly created  repository directory and start a new python virtual environment, upgrade pip, install wheel and activate the new virtual environment:
    ```
    $ cd Day3-EMSL-SummerSchool-2002
    $ python -m venv venv
    $ python -m pip install -U pip
    $ python -m pip install wheel
    $ source venv/bin/activate
    ```
    Find the installed version of Mono:

    ```
    $ find /Library/Frameworks/ -name mono-2.pc

    /Library/Frameworks/Mono.framework/Versions/6.12.0/lib/pkgconfig/mono-2.pc
    ```
    Replace {mono version here} in the next step with the version found on the previous step, which is 6.12.0

    ```
    $PKG_CONFIG_PATH=/Library/Frameworks/Mono.framework/Versions/{mono version}/lib/pkgconfig/ python -m pip install pythonnet
    ```
7. Install CoreMS, CoreMS dependencies, and Jupyter
    ``` 
    $ python -m pip install -r requirements.txt
    ```
8. Run Jupyter Notebook
    ```
    jupyter notebook
    ```
This should open the browser with the Jupiter notebook, open the Summer School CoreMS Tutorial notebook, and you are ready to go. 

# Windows Installation Instructions

1. Download Microsoft Build Tools for Visual Studio 2022 
https://aka.ms/vs/17/release/vs_BuildTools.exe  
•   During the installation of C++ build tools and make sure the latest version for these:
    - MSVCv142 - VS 2022 C++ x64/x86 build tools 
    - Windows 10 SDK

2. Download and install git:  
https://git-scm.com/download/

3. Download and install Python 3.9.13:
https://www.python.org/downloads/

4. At this point, you should have all the compilers and software frameworks needed to install CoreMS. Go ahead and use git to clone the Day 3 tutorial repository into a location of your choice. 
    ```
    $ git clone https://github.com/EMSL-Computing/Day3-EMSL-SummerSchool-2022
    ```  
5. After the cloning process, go to the newly created repository directory and start a new python virtual environment, upgrade pip, install wheel and activate the new virtual environment:
    ```
    $ cd Day3-EMSL-SummerSchool-2002
    $ python3 -m venv venv
    $ python3 -m pip install -U pip
    $ python3 -m pip install -U setuptools
    $ python3 -m pip install wheel
    $ venv/Scripts/activate
    ```
7. Install CoreMS, CoreMS dependencies, and Jupyter
    ``` 
    $ python3 -m pip install -r requirements.txt
    ```
8. Run Jupyter Notebook
    ```
    jupyter notebook
    ```


