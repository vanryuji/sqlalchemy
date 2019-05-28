# Overview
About sqlite engine

# Environments
* SQLAlchemy 1.3.3

# Foreign Key
SQLite supports FOREIGN KEY syntax when emitting CREATE statements for tables, however by default these constraints have no effect on the operation of the table.<br>
Constraint checking on SQLite has three prerequisites:
* At least version 3.6.19 of SQLite must be in use
* The SQLite library must be compiled without the SQLITE_OMIT_FOREIGN_KEY or SQLITE_OMIT_TRIGGER symbols enabled.
* The PRAGMA foreign_keys = ON statement must be emitted on all connections before use.

SQLAlchemy allows for the PRAGMA statement to be emitted automatically for new connections through the usage of events:
```python
from sqlalchemy.engine import Engine
from sqlalchemy import event

@event.listens_for(Engine, "connect")
def set_sqlite_pragma(dbapi_connection, connection_record):
    cursor = dbapi_connection.cursor()
    cursor.execute("PRAGMA foreign_keys=ON")
    cursor.close()
```
refer : https://docs.sqlalchemy.org/en/13/dialects/sqlite.html?highlight=sqlite#foreign-key-support
