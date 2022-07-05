
I would like the following available in the SAL and via citrix (or other)


# Anaconda 64bit

1) If you haven't already, install anaconda 64 bit https://www.anaconda.com/products/distribution#Downloads

2) Open the "anaconda prompt" on windows (not the powershell version) or "terminal" on mac

``` 
conda create -n spatial arcpy arcgis -c esri
conda activate spatial
conda install geopandas jupyterlab  matplotlib mapclassify -c conda-forge
pip install notebook geopy rtree
pip install --upgrade nbconvert

```

# VS Code

1) Please install [vscode](https://code.visualstudio.com/Download) 

2) Under extensions tab to the left install Python and Jupyter extensions, see [here for example](https://blog.openthreatresearch.com/installing_python_extension_vscode)

3) Check that vscode it has access to the `spatial` 

    - Open vscode, create a new file called `test.ipynb`.
    - When prompted select `spatial` as the "interpreter" or environment
    - write the following code in one of the cells
    ```
    import arcpy

    ```
    - Press `shift`+`enter` to execute it, when prompted select the `spatial` kernel from the dropdown.
    - There should be no error

