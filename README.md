# Local-First Backend Server
This repository lets you easily install and run a [Local-First Backend](https://github.com/Ben-Ryder/local-first-backend) server.  
It acts as a wrapper around the `@ben-ryder/lfb-server` package and means you don't have to clone the entire project monorepo or set up a new project from scratch just to run the server.

**Note:** This project is specifically for installing and running the server. If you wish to contribute or
see how it works, you can [view the server source code](https://github.com/Ben-Ryder/local-first-backend/tree/main/projects/server) in the main monorepo.

## Installation

### Prerequisites
You must have the following dependencies on your system or available via external providers to run the server:
- [Postgres](https://www.postgresql.org/) - used to store all users, changes etc
- [Redis](https://redis.io/) - used for short-lived storage and caching

### Setup

Start by cloning this repository:
```bash
git clone git@github.com:Ben-Ryder/lfb-server.git
```

You can then install dependencies with npm:
```bash
npm install
```

Then copy the `.env.example` file to `.env` and edit as required to configure secrets, the database, Redis etc.

### Database Setup
The server currently does not set up the database for you so this must be done manually.  
SQL scripts for doing this can be found in the `./scripts` folder:

```bash
cp scripts/example.setup.sql scripts/setup.sql
psql postgres -f ./scripts/setup.sql
```

## Usage
The server can be run via npm commands or directly via node.

With npm:
```bash
npm start
```

Directly with node:
```bash
node node_modules/@ben-ryder/lfb-server/build/src/main.js
```

## Updating
Updating to the latest server version is as simple as pulling the latest version from GitHub.  
This repository will be updated everytime a new release of the `@ben-ryder/lfb-server` package is made.  
To view release notes before updating you should [view the releases in the main project repository](https://github.com/Ben-Ryder/local-first-backend/releases).

## Deploying
This is a pretty standard node application so deploying to platforms such as [Fly.io](https://fly.io/) is straightforward.  
Simply configure the provider to install npm dependencies, run `npm start` and configure the environment variables as required.
