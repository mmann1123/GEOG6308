
I would like the following available in the SAL and via citrix (or other)


# Anaconda 64bit

1) Install anaconda 64 bit https://www.anaconda.com/products/distribution#Downloads

2) Open the "anaconda prompt" (not the powershell version)

``` 
conda create -n spatial arcpy=3.1 arcgis -c esri
conda activate spatial
conda install geopandas jupyterlab  matplotlib mapclassify -c conda-forge
pip install notebook geopy rtree
pip install --upgrade nbconvert

```

3) find the python path with and record it

`where python`

4) Students will need permission to write to the primary anaconda folder in order to install more modules - it should be `C:Program Files/Anaconda`. You can test whether permissions are working as expected by typing the following into the "anaconda prompt"

`conda install pandas -y`

This should install without an error.  

5) Copy the entire folder `C:\Program Files\ArcGIS\Pro\bin\Python\envs\arcgispro-py3` to the anaconda env folder based on the response from `where python`, should be something like `C:\Users\mmann\Anaconda3\envs\` to create a new folder with the path `C:\Users\mmann\Anaconda3\envs\arcgispro-py3`.

6) Insert an entry into `C:\Users\mmann\AppData\Roaming\Code\User\settings.json` with the path to the user's python executable in the new `arcgispro-py3` folder:

```
    "python.defaultInterpreterPath": "c:\\Users\\mmann\\Anaconda3\\envs\\arcgispro-py3\\python.exe",
```

Make sure not to delete other entries in `settings.json`. It might looks something like:

``` json
{
    "workbench.colorTheme": "Default Dark+",
    "security.workspace.trust.untrustedFiles": "open",
    "jupyter.interactiveWindowMode": "perFile",
    "python.formatting.provider": "black",
    "editor.formatOnType": true,
    "terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\cmd.exe",
    "[python]": {
        "editor.defaultFormatter": "ms-python.python"
    },
    "editor.formatOnSave": true,
    "jupyter.askForKernelRestart": false,
    "python.defaultInterpreterPath": "c:\\Users\\mmann\\Anaconda3\\envs\\arcgispro-py3\\python.exe",
}
```


# Sublime
1) install sublime

2) go to Preferences > settings.

3) in the right hand window, replace all text with:

```
{
    "ignored_packages":
    [
        "Vintage",
    ],

    "tab_size": 4,
    "translate_tabs_to_spaces": true
}
```

4) go to tools > build system > New Build System

5) replace all text with the following, but replace the path with the one found above using `where python`:
* NOTE: replace all \ with / in the path to python *

```

{
    "cmd": ["c:/Users/mmann/Anaconda3/envs/spatial/python.exe", "-u", "$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python"
}

```
6) Save the file as `spatial.sublime-build` in the default directory. 

## Validate
1) Create a new file in sublime, save it as test.py
2) Add the following lines:

``` python

import arcpy
import arcgis
print('hit')

```
3) Select spatial from Tools > Build System

4) Hit command B to build.

5) It should print 'hi', '[Finished in Xs]' and throw no errors in the bottom window

If that doesn't work use the following for the build configuration:
```

{
    "cmd": ["c:/Progra~1/ArcGIS/Pro/bin/Python/scripts/propy.bat", "-u", "$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python"
}   

``` 

# VS Code

1) Please install [vscode](https://code.visualstudio.com/Download) 

2) Under extensions tab to the left install Python and Jupyter extensions

3) Check that it has access to the `arcgispro-py3` 

    - Open vscode, create a new file called `test.ipynb`.
    - If prompted select `arcgispro-py3` as the "interpreter" or environment
    - write the folloing code in one of the cells
    
    ```
    import arcpy

    ```
    - Press `shift`+`enter` to execute it, when prompted select the `arcgispro-py3` kernel from the dropdown.
    - There should be no error

<!-- # Thonny

Before you start

- please ensure that VS 2013, VS 2015, VS 2017, VS 2019 or VS 2022 was installed with the Visual C++ option

- Install rust https://rustup.rs/ package manager

1) Download and install [Thonny](https://thonny.org/)

2) Go to Tools > Interpreter tab > from the dropdown select "Alternative Python 3 interpreter or virtual environment", and browse for the path found above using `where python` from the first section. 

3) Go to edit > preferences > Editor > Auto-Completion > switch "auto-show competer"  to "Always"

4) Go to Tools > Manage plugins > search for Jupyter > click on jupyter link > click install button


  -->
