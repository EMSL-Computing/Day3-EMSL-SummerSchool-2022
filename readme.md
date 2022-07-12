# Installation Instructions for MAC

1. Install Python 3.9.13 following this tutorial:
  https://www.chrisjmendez.com/2017/08/03/installing-multiple-versions-of-python-on-your-mac-using-homebrew/  
  By the end of the tutorial it, if you have not yet, set python 3.9.13 as the global option.  
  If you are using Z shell make sure to add the python path to your zprofile:  
  ```
  echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
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
Find the GCC version 
```
$ cd usr/local/bin
$ find gcc*  
gcc-11  
gcc-ar-11  
gcc-nm-11  
gcc-ranlib-11  

```
In this case the version is 11. Replace the label {version} in the next step, in this case the command is: "ls -s gcc-11 gcc"

```
$ ln -s g++-{version} g++ 
$ ln -s gcc-{version} gcc

```
call gcc --version to check everything is working

4. Install Mono, DotNet (this step is needed to install PythonNet which is used to read Thermo raw files)
```
$ brew install pkg-config
$ brew install mono-mdk
$ brew install mono
$ brew install dotnet
```
5. Clone the Day 3 tutorial repository
```
$ git clone "xxxxx"
```  
6. cd into the repository directory and start a new python virtual enviroment, upgrade pip and install wheel:
```
$ cd Day3-EMSL-SummerSchool-2002
$ python -m venv venv
$ python -m pip install -U pip
$ python -m pip install wheel
$ source venv/bin/activate
```
Find the installed version of Mono:

```
Locate mono-2.pc
/Library/Frameworks/Mono.framework/Versions/6.12.0/lib/pkgconfig/mono-2.pc
/usr/local/Cellar/mono/6.12.0.122_1/lib/pkgconfig/mono-2.pc
```
and install PythonNet (replace {mono version here} with the version found on the previous step) which is 6.12.0

```
$PKG_CONFIG_PATH=/Library/Frameworks/Mono.framework/Versions/{mono version}/lib/pkgconfig/ python -m pip install pythonnet
```
7. Install CoreMS and Jupyter
``` 
$ python -m pip install -r requirements.txt
```
8. Run Jupyter Notebook
```
jupyter notebook
```
# Installations Instructions for Windows

