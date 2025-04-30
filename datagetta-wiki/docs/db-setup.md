# Local DB Setup with Docker Guide

### 1. Pull the Latest Changes

Ensure your local repository is up to date by pulling the latest changes.

### 2. Shut Down Existing Containers

If the container for this project is already running, navigate to the main directory and run the following command in the terminal:

```sh
docker compose down -v
```

### 3. Remove Existing Data

Delete the `data` and `backups` folders if they exist in the main directory.

**Warning:** This action will **delete all data currently stored in the database**.

```sh
rm -rf data backups
```

### 4. Update Configuration File

Navigate to your `.env` file and ensure the following settings are correct for local development:

```.env
SQL_SERVER_NAME: "localhost"
SQL_PORT: "5433"
```

**Note:** This is for local development only. If running on the server, these values should be set as follows:

```.env
SQL_SERVER_NAME: "datagetta.cse.eng.auburn.edu"
SQL_PORT: "5432"
```

### 5. Start the Containers

In the main directory, bring up the containers in detached mode:

```sh
docker compose up -d
```

This will start the services defined in the `docker-compose.yml` file for local development.
