# User #

A user is a database level object. Each user maps to a login.

You can create a user using: `CREATE USER [user] FOR LOGIN [login]`. The convention is generally to user the same name for the user and the login.

You can optionally use `WITH DEFAULT_SCHEMA=[schema]` when creating the user, which specifies which schema unqualified object names will refer to (`[dbo]` is the default). 