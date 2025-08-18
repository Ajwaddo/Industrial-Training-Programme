# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Setup the Connection Between Dremio and Apache Superset](#setup-the-connection-between-dremio-and-apache-superset)


## Setup the Connection Between Dremio and Apache Superset
1. Create a new database connection in Superset.
2. For database type, choose other.
3. Enter the sqlalchemy URI in the required field.
4. dremio+flight://admin:XXXXXXXXXX@dremio.heitecharena.com:32010/minio?UseEncryption=false
5. Test the connection to the database.
6. Utilise the connection to the database.