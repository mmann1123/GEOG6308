# 1 - Installing Anaconda
Anaconda is a package manager for python. This will allow us to safely add and remove additional modules (functionality) to python. 

1) Go to [anaconda.com](https://www.anaconda.com/) and download the latest installer. 
	- Use all the defaults for the installation process

# 2 - Accessing Conda
When adding new modules to python we are going to need to run conda from your computers *command line*, this will be called different things on different systems. On a mac/linux its called the terminal window, on windows we have a few options but we will use an anaconda specific command prompt. 

## Windows
1) Go to the Start menu, look for "Anaconda Powershell Prompt", you will run conda from here

2) To test wether or not your install worked run the following command from the Powershell Prompt:

`conda info`

You should see a long description of the version on conda installed locally on your computer. 

*Problem Solving*: *IF `conda info` returned an error*, search for 'Environment' in the search bar, click "edit the system environment variables". Under the "Advanced" tab, click "Environment Variables..". In the upper box, highlight the row with 'Path', and clicke 'Edit', click "New", add the path to the Anaconda3 folder, which should be `C:\Users\username\Anaconda3`, Hit "OK" twice. Then close and reopen any open command prompt windows. 

## Mac
1) Open "Terminal"
	- If the top of the terminal says "zsh", run the following command in the terminal window:
	`chsh -s /bin/bash`
	- Enter your password
2) To test wether or not your install worked run the following command from the terminal:

`conda info`

You should see a long description of the version on conda installed locally on your computer. But confirm the PATH matches what you see on your computer. 

*Problem Solving*: *IF `conda info` returned an error*, add the following lines to the `~/.bash_profile` text document.  

```
[[ -s ~/.bashrc ]] && source ~/.bashrc
PATH="$PATH:~/Applications/anaconda3/bin:${PATH}"
export PATH
```

# 3 - Update Anaconda

1) From your terminal run the following:

`conda update conda`

then:

`conda update -n base conda`


# 4 - Install Jupyter Notebook

## Mac and Windows

1) Install an interactive development environment (IDE) called Jupyter Notebook in your base environment. Run the following:

`conda install notebook -c conda-forge`

The `-c conda-forge` is telling conda to install from a different `channel` called `conda-forge`. This is a user maintained repository of python modules that is often more up to date than condas default repository. 

# Use

For the following lectures in "Python Crash Course" we will use jupyter notebook. 

Here is the workflow:
1) `cd` to the folder holding your `.ipynb` files you want to work on.

`cd path/to/my/homework`

2) Activate the anaconda environment we want to work in.  You can think of the "environment" as a sandbox for python, where only the things you want for a specific project are available, and nothing else. For most tasks, you will create a specific conda environment and activate it. In this case we will just be using the `base` environment.

`conda activate base`

3) Then run jupyter notebook:

`jupyter notebook`

You should now be forwarded to a webpage showing the jupyter notebook interface. 
