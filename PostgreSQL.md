# By default, access to PostgreSQL database server is only from localhost.
$ sudo ss -tunelp | grep 5432

$ sudo vim /etc/postgresql/12/main/postgresql.conf

$ sudo vim /etc/postgresql/12/main/pg_hba.conf

listen_addresses = '*'

sudo systemctl restart postgresql

# Check for listening port 
sudo ss -tunelp | grep 5432

# if you have an active UFW firewall, allow port 5432
sudo ufw allow 5432/tcp


# Connect and change postgres password
$ sudo su - postgres
postgres@os1:~$ psql -c "alter user postgres with password 'StrongPassword'"
ALTER ROLE

# Add a test database user:
createuser deployer

# Add the test database and grant ownership to deployer:
postgres@debian:~$ createdb test_db -O deployer


# Login to test_db database:

~$ psql -l  | grep test_db
 test_db    | test_user1  | LATIN1   | en_US   | en_US |
~$ psql test_db

# Set user password
testdb=# alter user deployer with password 'MyDBpassword';
ALTER ROLE

# Set user to SuperUser
ALTER USER deployer WITH SUPERUSER;

# Create a table and add some dummy data:

testdb=# create table test_table ( id int,first_name text, last_name text );
CREATE TABLE
testdb=# insert into test_table (id,first_name,last_name) values (1,'John','Doe');
INSERT 0 1

