# Logins #

A login is a server level object. It is used to log in to SQL Server.

## Windows Account ##
A login can be created from a Windows account: `CREATE LOGIN [domain\user] FROM WINDOWS`.

## SQL Server Exclusive Login ##
A login can also be created exclusively for SQL Server: `CREATE LOGIN [login] WITH PASSWORD = N'password'`

The following options are available:

- `MUST_CHANGE` - the password must be changed on the first login
- `CHECK_POLICY = ON` - the password must match the Active Directory password policy
- `CHECK_EXPIRATION = ON` - the password expiration policy from Active Directory is enforced

SQL authentication must be turned on to use SQL Server logins
