# Role #

A role is a database level object. It is a group of users which permissions can be assigned to.

A role can be created using: `CREATE ROLE [role]`.

Users can be added to roles using: `ALTER ROLE [role] ADD MEMBER [user]`.

Permissions can be given to a role using: `GRANT [permission] TO [role]`. A single user can also be used in place of a role.

A permission can be granted for a single object using: `GRANT [permission] ON [object] TO [role]`. For example, to allow a role to execute the stored procedure `spCreateSale`, use: `GRANT EXECUTE ON [dbo].[spCreateSale] TO [role]`.