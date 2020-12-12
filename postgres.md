# Redis

We will install PostgreSQL with PostGIS using Postgres.app.

## Do you need this?

If you have a working PostgreSQL database and no problems, consider keeping that. These instructions assume you have do not have a working database.

## Save your data directory

If you have an existing or broken installation:

1. Stop the PostgreSQL servers.
1. Copy your data directory to a safe temporary location and make a backup. I will assume ~/Desktop/postgres
1. Remove the existing PostgreSQL installation.

Note that if you have (the remnant of) a brew installation, your data directory is probably `/usr/local/var/postgres`.

## Install PostgreSQL and PostGIS

Go to https://postgresapp.com and follow instructions. You now have a PostgreSQL server ready to roll. Embrace the black box. I prefer this over `brew install postgis`, because that keeps breaking for me.

## No data?

Start a new cluster of your choice. Instructions are at https://postgresapp.com.

## Restoring your data directory

You will need to create a database cluster of the same major version your previous installation was running. I will assume Postgres 12.

1. Create a Postgres 12 cluster. We will assume the name `pg12`.
1. The default location is `~/Library/Application Support/Postgres/pg12`, that is fine.
1. Confirm the server starts.
1. Stop the server.
1. Copy your saved data directory over the newly created `~/Library/Application Support/Postgres/pg12`. Say yes to replacing whenever it is asked.
1. Start the server. It should work. If not, either start with a clean cluster or Google any errors.
