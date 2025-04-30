# Local App Setup (Inhereted Structure)

_Last Updated 3/24/25 by Tyler Teufel_

## 1. (If Needed) Install Necessary Frameworks / Tools Locally

The first step in getting this project setup for local development is to make sure your machine has the necessary local dependencies. Though some might already have these installed, in the case that you do not, the following must be installed in order to run the project locally:

- [Docker Desktop (Windows)](https://docs.docker.com/desktop/setup/install/windows-install/) , [Docker Desktop (Mac)](https://docs.docker.com/desktop/setup/install/mac-install/), or [Docker Desktop (Linux)](https://docs.docker.com/desktop/setup/install/linux/ubuntu/)
- [Node.js](https://nodejs.org/en/download) (See drop down for different Operating Systems Options)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## 2. Clone Repo Locally from GitHub

The next step is to clone the remote GitHub repository locally for development. Once you are in the desired directory to store the project folder in, run the following command:

```bash
git clone https://github.com/tyler-teufel/datagetta.git
```

From here, you can `cd` into the generated folder to access the project in its git repository, and develop in your desired IDE.

## 3. Install Node Dependencies

If you have not already, run the following command to enter the project folder. If you have already opened the project folder in your IDE of choice, you may skip this step.

```bash
cd datagetta
```

Once in the project repo directory, the next step will be to navigate into the UI folder to install the node package dependencies needed to make the Next.js project and any additionally used packages operate as intended:

```bash
cd dg-frontend
npm install
```

You can past both lines into the terminal and they should execute sequentially; however feel free to enter them one at a time as well.

If any errors are encountered, double check that you have installed Node correctly, and that it is at least version 21.

**Please Note: This may take a minute or so upon the first installation. This is a large project, so if you see the animated spinning loader icon in the terminal, it should be working as intended.**

## 3. Pull the Required Docker Images from Remote Registry

Next, we need to pull the 3 images needed to run the project into your local docker environment, which have the correct image versions configured in the `docker-compose.yaml` file.

To pull the images from the remote registry, run the following:

```bash
docker compose pull
```

If your system does not recognize docker for whatever reason, please verify the installation worked correctly.

## Run the Docker Compose File to Start the Containers

In order to have the pulled docker images begin to run as containers, allowing your project to get started, run the following command from the outer directory, with the locally configured `docker-compose.override.yaml` file:

```bash
docker compose -f up -d
```

It is imperative that, when working locally, you ensure you utilize the overflow file such that you are not using the prod setup.

The terminal should show the containers starting, and finish with dialog that either says `started` or `running`.

From here, open up your browser and navigate to `localhost:3000` to access the Next.js web app.

## 4. Setup Python Environment

To get setup with the parser locally, first you want to navigate back to the home directory of the project, and setup your venv:

```bash
cd .. # This should take you back to the root directory /datagetta
```

Once in the root directory, run the following to create your venv with the closest python version you have to `3.10`:

For Unix based OS (Mac / Linux):

```bash
python3.10 -m venv dg-env
source dg-env/bin/activate
```

For Windows:

```bash
python3.10 -m venv dg-env
source dg-env/Scripts/activate
```

Please note - you do not have to install 3.10 if you do not have it. Simply use the lowest python version you have.

Next, you need to navigate to the parser directory:

```bash
cd csvparser/src
```

Once you are in src, you need to install the python package dependencies in the venv. Make sure to first verify that your terminal is using the correct python venv:

```bash
which python3 # Or which python for windows
```

If the returned path leads to your venv folder, then you are ready to continue. You then install the dependencies using `pip`:

```bash
pip3 install -r requirements.txt
```

for more info regarding package updates, see that wiki page [here](Dependency-Updates.md).

## 5. Run Parser

**Please note - you can also run this directly in the container; however this is how I (Tyler) have been going about it.**

In the `src` directory, running the parser is as easy as this command:

```bash
python3 ftpPuller.py
```

**Please note - this will take several hours!**
