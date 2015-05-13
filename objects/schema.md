# Schema #

A schema is a database level object. It can be used to group objects for permissions, as well as for organising objects.

A schema can be created using: `CREATE SCHEMA [schema] [AUTHORIZATION [owner_name]]`.

The owner of a schema can be modified using: `ALTER AUTHORIZATION ON SCHEMA::[schema] TO [owner_name]`.

`SCHEMA::` is a scope qualifier. `OBJECT::` is the default qualifier.