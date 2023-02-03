## Install GNU Octave

### Windows
Download and run .exe file from https://octave.org/download#ms-windows
### Mac
Use Homebrew (https://wiki.octave.org/Octave_for_macOS)
```
brew update
brew upgrade
brew install octave
octave --gui
```
### Linux
Follow the installation instructions below for pre-compiled Octave for Debian.
```
apt-get update
apt-get -y install curl wget nano libgraphicsmagick++1-dev libsuitesparse-dev libqrupdate1 libreadline7 libfftw3-3 libhdf5-100 libgl1 libglu1-mesa libgl2ps1.4 \
        libcurl4-gnutls-dev libarpack2 libopenblas-base git gnuplot libqt5gui5 libqt5core5a

mkdir /content

LOCATION=$(curl -s https://api.github.com/repos/cerr/octave-colab/releases/latest \
| awk -F\" '/browser_download_url/ { print $4 }') && curl -L -o /content/octavecolab.tar.gz $LOCATION
 
cd /content && tar xzvf /content/octavecolab.tar.gz
chmod -R 777 /content

export OCTAVE_EXECUTABLE=/content/octave/bin/octave-cli
```
## Set Java, Octave and Python paths
### Set JAVA_HOME env var
Add `JAVA_HOME` environment variables to point to location to point to Java Runtime. For eample, on Windows set `JAVA_HOME` as `C:\Program Files\Java\jre1.8.0_351` 

### Set OCTAVE_EXECUTABLE env var
For example, on Windows set `OCTAVE_EXECUTABLE` as `C:\Program Files\GNU Octave\Octave-7.3.0\mingw64\bin\octave-cli.exe`

## Install CERR
Download CERR from GitHub to a desired location as follows.
```
cd C:/software/cerr
git clone --single-branch --branch octave_dev https://www.github.com/cerr/CERR.git
```

## Create Conda environment 

Step1: Install Miniconda following the instructions at https://docs.conda.io/en/latest/miniconda.html

Step 2: Download the requirements file from https://github.com/stratis-forge/installation-and-dependencies/blob/main/requirements_windows.yml. 
```
cd C:/software/stratis-forge
git clone https://github.com/stratis-forge/installation-and-dependencies.git
```
Note that the requirements file can be extended as needed by the user to use additional packages. An updated requirements file along with the analysis workflow can then be pushed back to stratis-forge via a pull request.

Step 3: Build conda environment 
Then issue the following command from Miniconda prompt to create the environment. Note that it is assumed that Miniconda in installed under C:/Users/username/Miniconda3. Please use the correct location of Miniconda.
```
conda env create -f C:/software/stratis-forge/installation-and-dependencies/requirements_windows.txt \
   -p C:/Users/username/Miniconda3/envs/stratis
```

Step 4: Activate the newly created environment

Issue the following command from Miniconda prompt:
```
conda activate C:/Users/username/Miniconda3/envs/stratis
```

Step 5: Start Jupyter lab server.

Issue the following command from Miniconda prompt:
```
jupyter lab
```

Step 6: To deactivate/activate the current environment

Issue the following command from Miniconda prompt:
```
conda deactivate
```

## Install Octave packages

### Set environment variables required for the Pythonic package
For example, on Windows
```
C:> set PYTHONHOME=C:\Users\username\Miniconda3
C:> set PYTHONPATH=C:\Users\username\Miniconda3
C:> set PYTHON=C:\Users\username\Miniconda3\python.exe
```

### Open Octave and install
#### For example, on Windows
`C:> "C:\Program Files\GNU Octave\Octave-7.3.0\mingw64\bin\octave.bat" `
#### Install packages from Octave command line
```
octave:1> pkg install -forge io;
octave:2> pkg install -forge statistics; 
octave:3> pkg install -forge image;
octave:4> pkg install https://gitlab.com/mtmiller/octave-pythonic/-/archive/master/octave-pythonic-master.tar.gz
```


## Tips to debug installation issues:
* On Mac: graphics_toolkit related error can be resolved by running the following in terminal
```
echo "set enable-bracketed-paste off" > .inputrc
export INPUTRC=$PWD/.inputrc
```
* On Windows, MinGW or .NET installation might be required. MinGW can be installed from https://www.mingw-w64.org/downloads/#mingw-builds if you run into a related error. 
* GNU Octave uses Qt for graphics. Install Qt at https://www.qt.io/download-qt-installer if you run into a related error.

