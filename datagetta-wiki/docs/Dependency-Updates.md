# Updating Dependency Usage

In the back-end of this project we utilize several different Python packages throughout our scripts. In order to avoid dependency issues from platform to platform, (whether that be for each dev's local instance or simply for our production environment), we keep a requirements.txt file within the csvparser directory containing all packages and versions utilizes.

Below is a step by step guide to follow for both new contributors or existing contributors such that everything stays constant across our project.

## For New Contributors / New Versions

For this section, you ideally are someone who is working with the Python scripts on the back-end (locally) for the first time, or are working on a version / branch of the project that you have not worked in yet. This will ensure that you get the correct packages and versions installed.

### 1. Setup local virtual environment

The below instructions are written in the context of the directory setup as of 2/12/25. If reorganized by the time this wiki is being used, interpret the any references to the. folder "csvparser" or its subsequent child directories as which ever folders contain all of the Python related back-end.

**If you have yet to create a `venv` for this project, click [here](venv-setup.md) for quick instructions.**

To begin, you need to source you virtual environment (if not already done):

**MacOS (zsh):**

```bash

source venv-name/bin/activate

```

Once your terminal prompt has `(venv-name)` appended to the beginning, then you know you are within the venv.

### Navigate to back-end directory

Once you have the venv sourced, you need to navigate to the directory within the project that contains the `requirements.txt` file, assuming you are starting from the base directory `~/datagetta`:

```bash

cd csvparser

```

### Install the correct package dependencies

Once you are in the correct directory, you are ready to install the correct package versions into your venv.

Assuming you already have Python and pip installed, run the following command to install all packages in one shot:

```bash

pip3 install -r requirements.txt

```

Assuming no errors have occurred, you will see all of the packages begin to install in your terminal environment. If any version errors are encountered, please ensure you have the correct requirements.txt for your branch.

## For Current Dev's and Contributors

For the following, it is assumed that you have already been working with this environment, and have, for whatever reason, installed new packages to be used with the project.

### Ensure you are in correct directory

It is imperative that you ensure you are back in the same directory as the `requirements.txt` file. This is just a step to make sure you are not still in the `src/` directory.

The correct directory is: `~/datagetta/csvparser`.

### Freeze the current dependencies to the requirements file

Run the following pip command in terminal to correctly update the requirements.txt file:

```bash

pip3 freeze > requirements.txt

```

After this, you should not see anything else outputted into the terminal besides your usual prompt. You are now ready to commit your changes, assuming everything works.
