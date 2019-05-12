# Overview
SQLAlchemy tutorial<br>
SQLAlchemy : The Python SQL Toolkit and Object Relational Mapper<br>

# Environments
* Python 3.6.7
* SQLAlchemy 1.3.3

# Use another DBMS
```shell
# pymysql
# https://docs.sqlalchemy.org/en/13/dialects/mysql.html?highlight=mysql#module-sqlalchemy.dialects.mysql.pymysql
engine = create_engine('mysql+pymysql://<username>:<password>@<host>/<dbname>[?<options>]', echo=True)
...
class User(Base):
    __tablename__ = 'users'
    
    id = Column(Integer, primary_key=True)
    name = Column(String(10))
    fullname = Column(String(10))
    nickname = Column(String(10))
...
```

# Reference
* https://docs.sqlalchemy.org/en/13/orm/tutorial.html
