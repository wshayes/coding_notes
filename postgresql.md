# Postgresql

- https://github.com/dimitri/pgcopydb
- https://github.com/orgrim/pg_back - backup tool to make postgres backups faster and easier
- https://gobackup.github.io/ - Maybe as a database backup tool - significant Chinese developers involvement
- 

## Useful commands

```python
pg_dump --file=sites_dev.dump --dbname sites_dev --clean --format=custom --username=sites --host=localhost --port=5432 
```

```python
pg_restore --dbname=sites_stage --username=sites --host=localhost --format=custom --create --clean  sites_dev.dump
```

## psql or pgcli commands

- list databases
    - `\l`
- create db from another one
    - `create DATABASE sites_stage with template sites_dev owner sites;`

## Appsfolio notes

**create** **role** appsfolio **with** createdb createrole **password** **'xxx'**;

**alter** **role** appsfolio createdb createrole login;

**create** **database** appsfolio_dev **with** **owner** = **"appsfolio"**;

**grant** appsfolio **to** postgres;

### Server mgmt

```html
sudo systemctl status|start|stop|restart postgresql

# Open client from Mac to Odin for postgres database using .pgpass and SSH tunnel (port 5432)
psql -h localhost -U ubuntu postgres

sudo -u postgres psql
sudo -u postgres createuser <username>
sudo -u postgres createdb <dbname>
```

### psql SQL commands

```sql
CREATE DATABASE yourdbname;
CREATE USER youruser WITH ENCRYPTED PASSWORD 'yourpass';
ALTER USER youruser WITH PASSWORD 'yourpass';
GRANT ALL PRIVILEGES ON DATABASE yourdbname TO youruser;
CREATE SCHEMA yourschema;

# Role mgmt (easiest to do in PGAdmin)
GRANT CONNECT ON DATABASE yourdbname TO youruser;
GRANT USAGE ON SCHEMA yourschema TO youruser; # to get access to Schema
GRANT ALL ON ALL TABLES IN SCHEMA yourschema TO youruser;  # after CONNECT/USAGE to get admin access to Schema
ALTER DEFAULT PRIVILEGES IN SCHEMA yourschema GRANT [ALL|SELECT] ON TABLES TO youruser;
GRANT SELECT ON ALL TABLES IN SCHEMA yourschema TO youruser_readonly; # read only access to tables in Schema
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA yourschema TO youruser;

# Cleaning up Schema tables
SET SEARCH_PATH="sites";
SHOW SEARCH_PATH;

# PSQL script to drop all tables in current Schema (e.g. see SET SEARCH_PATH above)
do $$ declare
    r record;
begin
    for r in (select tablename from pg_tables where schemaname = 'sites') loop
        execute 'drop table if exists ' || quote_ident(r.tablename) || ' cascade';
    end loop;
end $$;
```

### psql Meta commands

```bash

\dp # list all tables and their permissions
\du # list all users
\dn # list all schemas
\dx # list all loaded extensions

\l # list all databases
\h <command> # provide help on the command - e.g. \h select
\password  # change current user's password
\timing on|off  # show timing for queries
\watch <seconds> # run current query buffer every X seconds
```

## Extensions

```sql
SELECT * from pg_extensions;
CREATE EXTENSION 'auto_explain';
ALTER EXTENSION extension_name UPDATE;
DROP EXTENSION extension_name;

\dx - show all extensions loaded

sudo apt install postgresql-16-pgvector # installs the vector extension

select * from pg_available_extensions order by name; # list all AVAILABLE extensions
```