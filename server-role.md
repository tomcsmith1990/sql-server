# Server Roles #

A server role is a server level object. It is a group of logins which permissions can be assigned to.

A server role can be created using: `CREATE SERVER ROLE [role]`.

A login can be added to a server role using `ALTER SERVER ROLE [role] ADD MEMBER [login]`.

## Permissions ##

You can view the server level permissions which a server role has using: `sp_srvrolepermission 'role'`.

You can grant permissions to a server role using: `GRANT permission[,permission2,...,permissionN] TO [role]`. A single login can also be used in place of a role.

A permission has three states:

- `GRANT` - can use this permission
- `WITH GRANT` - can grant this permission to others
- `DENY` - cannot use this permission

You can give a role a permission plus the ability to grant that permission to others using: `GRANT permission TO [role] WITH GRANT OPTION`

