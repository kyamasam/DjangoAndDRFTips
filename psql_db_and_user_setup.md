### Login as admin

```
sudo -u postgres psql
```

### Create database
```
create database rde;
```
### Create database
```
create database yourdbname;
```
### Create user
```
create user yourusername with password 'yourstrongpassword';
```

### DB Optimizations
We are setting the default encoding to UTF-8, which Django expects. We are also setting the default transaction isolation scheme to “read committed”, which blocks reads from uncommitted transactions. Lastly, we are setting the timezone. By default, our Django projects will be set to use UTC. These are all recommendations from the Django project [itself]('https://docs.djangoproject.com/en/1.9/ref/databases/#optimizing-postgresql-s-configuration'):

```
ALTER ROLE yourusername SET client_encoding TO 'utf8';
ALTER ROLE yourusername SET default_transaction_isolation TO 'read committed';
ALTER ROLE yourusername SET timezone TO 'UTC';

```

### Granting User privileges

```
GRANT ALL PRIVILEGES ON DATABASE yourdbname TO yourusername;
```