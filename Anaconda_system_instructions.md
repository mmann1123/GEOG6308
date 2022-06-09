
# Anaconda 64bit

1) Install anaconda 64 bit https://www.anaconda.com/products/distribution#Downloads

2) Open the "anaconda prompt" (not the powershell version)

``` 
conda create -n spatial arcpy arcgis -c esri
conda activate spatial
conda install geopandas  -c conda-forge
pip install notebook
pip install --upgrade nbconvert
```

3) find the python path with and record it

`where python`

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
6) Save the file as spatial.sublime-build in the default directory. 

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

# Arcgis

Likely requires install of node.js

``` 
conda create -n arcgis arcgis -c esri -y
conda activate arcgis
conda install geopandas -c conda-forge -y
pip install notebook
pip install --upgrade nbconvert
```

# VS Code

1) Please install [vscode](https://code.visualstudio.com/Download) 
2) Under extensions tab to the left install Python and Jupyter extensions