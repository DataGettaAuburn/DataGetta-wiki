# CAS setup for datagetta
This document describes how to setup your environment to allow for CAS authentication


## Local Environment
**Testing CAS locally requires the setup of a local CAS server, as the Auburn CAS server only authorizes apps within the auburn.edu namespace. You may have to change the validator type to CAS30 in api/route/[client]/route.ts also for authentication to work with the local CAS server. For information on setting up a local CAS server, check out the examples from this github repo: https://github.com/uhawaii-system-its-ti-iam/next-cas-client. If you are not testing CAS on your local build, remember to set NEXT_PUBLIC_DISABLE_AUTH=1** 

```
NEXT_PUBLIC_BASE_URL=http(s)://<app-url>
NEXT_PUBLIC_CAS_URL=https://<cas-url>/cas

# PLEASE GENERATE YOUR OWN 32 CHARACTER LONG PASSWORD
NEXT_CAS_CLIENT_SECRET=[PASSWORD]

# ONLY SET TO 0 IF TESTING LOCALLY
NODE_TLS_REJECT_UNAUTHORIZED=0

NEXT_PUBLIC_DISABLE_AUTH=1
```

Both app-url and cas-url must be your local ip address followed by the port for each program. Using localhost may lead to issues with authentication.

Place the env file in the base directory of your next app.


## Dev Test Environment
Set up the env file as follows:

```
NEXT_PUBLIC_BASE_URL=https://datagetta-devtest.eng.auburn.edu
NEXT_PUBLIC_CAS_URL=https://authenticate.auburn.edu/cas

# PLEASE GENERATE YOUR OWN 32 CHARACTER LONG PASSWORD
NEXT_CAS_CLIENT_SECRET=[PASSWORD]

# ONLY SET TO 0 IF TESTING LOCALLY
NODE_TLS_REJECT_UNAUTHORIZED=1

NEXT_PUBLIC_DISABLE_AUTH=0
```

Store these env variables in GitHub secrets.


## Production Environment
Set up the env file as follows:

```
NEXT_PUBLIC_BASE_URL=https://datagetta.auburn.edu
NEXT_PUBLIC_CAS_URL=https://authenticate.auburn.edu/cas

# PLEASE GENERATE YOUR OWN 32 CHARACTER LONG PASSWORD
NEXT_CAS_CLIENT_SECRET=[PASSWORD]

# ONLY SET TO 0 IF TESTING LOCALLY
NODE_TLS_REJECT_UNAUTHORIZED=1

NEXT_PUBLIC_DISABLE_AUTH=0
```

Store these env variables in GitHub secrets.
