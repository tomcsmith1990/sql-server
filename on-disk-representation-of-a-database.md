# On-Disk Representation of a Database #

Creating a database generates two files:

- the *master data file* (`*.mdf`) contains the actual data
- the *log data file* (`*.ldf`) is the transaction log file, used for recovery

Dropping a database deletes these two files.
