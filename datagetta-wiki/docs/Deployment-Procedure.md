# Deploying New Changes to Production

With the newly deployed production environment, we have successfully setup a Github Self-Hosted Runner on the OIT provided VM such that with every PR that is merged or change pushed to `main` a our actions script is triggered.

## Self Hosted Runner Overview

By using a [Self-Hosted Runner](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners), we avoid the minute limitations and potential costs that are associated with GitHub runners, by leveraging the Ubuntu server that we have been provided with. The current runner is connected to the account of [tyler-teufel](https://github.com/tyler-teufel) at the time of the writing of this document, and is directly connected to this repository. For instructions on how this Self Hosted Runner was setup, see the following:

-  [Youtube Tutorial](https://www.youtube.com/watch?v=aLHyPZO0Fy0)
-  [GitHub Gist Tutorial Post](https://gist.github.com/devinschumacher/c503cead206d4992d1a3cbb03c95e4c9)

Following the following tutorials can provide some insight into how everything is setup.

## Secrets

In terms of the secrets that are traditionally utilized within a `.env` file for local development, we store them within the actions secrets within the repository. If you navigate to the repository settings and head to the 'secrets & variables' tab, and then select 'actions', you can add or modify any secrets needed.

The secrets are then routed utilizing injection code within both the `production.yml` actions script, as well as the `docker-compose.yaml` file. These secrets are first accessed from the repository using `secrets.SECRET_NAME` under the `env:` section of the actions script. To ensure these variables can be used within all run steps, inject this within the `deploy:` section right after the line showing `runs-on: self-hosted`. Doing this allows for each subsequent job to have access the all of the variables within the environment itself. From here, think of the variables as being injected at runtime into the project environment.

The next step is to inject these into the `docker-compose.yaml` file. Due to the way Docker is setup, it automatically tries to look for a .env file in the environment for the secrets. Since there is not one in this setup, we need to utilize an intuitive workaround that does not intervene with our `docker-compose.override.yaml` file we use for local development. This can be done by creating a section within the `docker-compose.yaml` file called `x-common-env` that would contain environmental variable injections that can be used as if it were in fact the contents of a `.env` file.

By including this object within each container using the `environment: <<: *common-env` syntax in each containers configuration, we successfully allow for these secrets to now exist in the projects environment.


## Deployment Triggers

Our current deployment script is configured to act as soon as a PR is successfully merged into the `main` branch. Currently, for good practice, we have all PRs to `main` requiring at least one review before allowing them to be merged directly to the branch. We also have added branch protection preventing any deletion of the branch, as well as pushing commit directly to main.

Any commits to `main` trigger the action to run, which consist of first granting necessary modification permissions to the directory of the project. Next, the docker containers are then confirmed to build. Following this, any existing containers are shut down, followed by the redeployment of the newly modified containers.

