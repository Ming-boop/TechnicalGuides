# Conda Setup Tutorial

This tutorial is developed using guidance from ChatGPT 4.0 as of December 18, 2024, and has been tested on the Windows 11 platform.

## Step 1. Setting Up Anaconda

### 1.1 Install Anaconda

Download Anaconda from [Anaconda's official website](https://www.anaconda.com/).

### 1.2 Verify Installation

After installation, open a terminal or Anaconda Prompt and type the following command to verify that Anaconda is installed properly:

```shell
conda --version
```

Maybe you need to add the following paths to system **environment variables** (depending on where Anaconda is installed):

```shell
<Installed Path>/Anaconda3
<Installed Path>/Anaconda3/Scripts
```

### 1.3 Create a New Conda Environment

It's a good practice to create a new virtual environment for each project to avoid dependency conflicts. Before starting a project, familiarize yourself with the following commands:

```shell
conda create --name <env_name> python=<version>
```

For example,

```shell
conda create --name myenv python=3.9
```

This creates a new environment called *myenv* with Python 3.9 installed.

* To activate certain environment:

```shell
conda activate <env_name>
```

* To deactivate the environment:

```shell
conda deactivate
```

* To view the list of environments:

```shell
conda info --envs
```

or

``` shell
conda env list
```

* To remove an environment:

```shell
conda env remove --name <env_name>
```

## Step 2. Setting Up a Python Project

### 2.1 Create Project Folder

Let’s organize the project structure. For example:

```shell
mkdir <project_name>
cd <project_name>
```

### 2.2 Create a Virtual Environment

As mentioned earlier, it’s good practice to create a virtual environment for each project to avoid conflicts with other projects. Since we already created myenv, you can either use that or create a new one dedicated to this project.

```shell
conda create --name <project_name_env> python=<version>
```

Activate the environment:

```shell
conda activate <project_name_env>
```

### 2.3 Install Necessary Packages

```shell
conda install <package_name>
```

or

```shell
pip install <package_name>
```

### 2.4 Managing Dependencies with requirements.txt

To ensure that others (or your future self) can recreate the project environment, it’s a good idea to create a *requirements.txt* file.

```shell
pip freeze > requirements.txt
```

This file will contain all the dependencies your project needs. You can share it with others, and they can install the exact dependencies by running:

```shell
pip install -r requirements.txt
```

## Miscellaneous

### 1. Resolving PowerShell Execution Policy Issues

Virtual environments might fail to activate due to **PowerShell execution policies**. To verify the current local execution policy, run the following command:

```powershell
Get-ExecutionPolicy -List
```

If the default policy is set to **Restricted**, it can prevent the virtual environment from activating. To remove the restriction, run the following command:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
```

### 2. Default Environment Location

When you create an environment using conda create, the environment is generated within the Anaconda installation directory (or wherever Anaconda is installed) by default. Specifically, it’s located in the *envs* folder under your Anaconda installation directory.

* Windows:

```shell
<Installed Path>/Anaconda3/envs/<env_name>
```

* macOS/Linux:

```shell
/home/<Username>/anaconda3/envs/<env_name>
```
