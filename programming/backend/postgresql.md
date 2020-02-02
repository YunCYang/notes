# PostgreSQL

## Basic Command
Use the below code to quickly execute a simple command and then exit psql.
`psql -c '(code here)'`
Or use psql to enter the inter terminal. '\q' to exit.

Another example of an commonly used command (for me at least).
`psql (database name) -f (file location)`
The above code executes the sql file at the file location.

## Roles
Use '\du' to list all roles in the database server.
Superuser bypasses all permission checks, excepts the right to log in.

When deploying site to AWS (Ubuntu), the following command temporarily elevates the permission to *superuser*.
`sudo su postgres -c psql`

PostgreSQL use roles to manage database access permissions. A role has different privileges including login, superuser, database creation, role creation, password, etc.

A role can contain other user roles (called a group role). A group role can also contain another group role, but looping is impossible.

Example command:
`CREATE ROLE miriam WITH LOGIN PASSWORD 'jw8s0F4' VALID UNTIL '2020-02-02'`

Note that `CREATE ROLE` and `CREATE USER` is identical except for one difference: with `ROLE` the default for `LOGIN` is `NOLOGIN`, but with `USER` the default is `LOGIN`.

Use `DROP ROLE (role name)` to remove roles.

### User and Group

To add a user role to a group role:
`GRANT (group role) to (user role)`

To remove:
`REVOKE (group role) FROM (user role)`

THe attribute `INHERIT` and `NOINHERIT` from the user role determines if the user role can automatically have the privileges of the group role.

If the user role did not inherit from the group role, use the following command to give the user role privileges from the group role:
`SET ROLE (user role)`

`RESET ROLE` reset to the original privilege.

### Login
To login:
`psql -d (database name) -U (user name)` to connect to a specific database.

Or `psql -h (server name) -d (database name) -U (user name)`

To check information about connection, use the command '\conninfo'.

To change user and database: `\c (new database) (new user)`, substitute database for '-' if you want to stay at the current database.

## Resource
- [Official Documentation](https://www.postgresql.org/docs/)
- [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)

[Back](../../README.md)
