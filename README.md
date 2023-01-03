## Installing dependencies for STRATIS workflows

STRATIS workflows use various image processing libraries for data transformation, registration and segmentation. The workflows that use [CERR](https://www.github.com/cerr) for feature extraction and image segmentaition require GNU Octave to be installed on the host computer. GNU Octave can be downloaded for Windows and Mac following instructions at https://octave.org/download. For Linux, please download the pre-compiled Octave with Java following instructions at https://github.com/stratis-forge/installation-and-dependencies/main/install_octave_linux.ipynb. On Windows, MinGW or .NET is required to use octave_cli within oct2py. MinGW can be installed from https://www.mingw-w64.org/downloads/#mingw-builds. Add `JAVA_HOME` and `OCTAVE_EXECUTABLE` environment variables to point to the respective Java Runtime and GNU Octave locations.


## Creating Conda environment for STRATIS 

Step1: Install Miniconda following the instructions at https://docs.conda.io/en/latest/miniconda.html

Step 2: Download requirements file for your OS from https://github.com/stratis-forge/installation-and-dependencies. Note that the requirements file can be extended as needed by the user to use additional packages.

Step 3: Build conda environment 

Issue the following command from Miniconda prompt:
```
conda env create -f C:/software/stratis-forge/installation-and-dependencies\requirements_win.txt \
   -p C:\Users\username\Miniconda3\envs\stratis
```

Step 4: Activate the newly created environment

Issue the following command from Miniconda prompt:
```
conda activate C:\Users\username\Miniconda3\envs\stratis
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
