# ansible-cromwell-database

This playbook creates a database that can be used by a cromwell server, or when
using cromwell to run a workflow.

The cromwell database does the following:
- Install a mysql database (using geerlingguy's mysql role)
- Set up an ufw firewall to make sure port 3306 can be accessed.

## Settings
Settings can be changed in the playbook itself. The default settings run a
mysql server at port 3306 that can be used by cromwell adding this to cromwell's configuration:
```HOCON
database {
  db.url = "jdbc:mysql://<<CROMWELL_DB_IP>>/cromwell_db?useSSL=false&rewriteBatchedStatements=true"
  db.user = "cromwell"
  db.password = "cromwell"
  db.driver = "com.mysql.jdbc.Driver"
  profile = "slick.jdbc.MySQLProfile$"
}
```
