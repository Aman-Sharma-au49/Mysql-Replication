MySQL Replication Setup

  

[Introduction 1](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.7cdnkteirdld)

[Servers 1](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.6q97atn9zh60)

[Installation on All Servers 1](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.pdk4uaedmxyp)

[Master Server (aman: 192.168.1.68) 2](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.r26towb2y8z2)

[Configure MySQL 2](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.n4y8t6dgpgg9)

[Create Replication Users 3](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.7bry5rmz56n7)

[On Slave 1 (first-vm: 192.168.122.37) 3](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.4okuokloetif)

[Configure MySQL 3](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.ixusgko5fxvk)

[Login to MySQL and execute: 4](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.ht7ofno36duq)

[● Create Replication Users 5](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.epfrxau6mq3p)

[Login to MySQL and execute: 5](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.m73eq5r3qdqt)

[On Slave 2(new: 192.168.122.111) 5](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.mty1semjr26g)

[Configure MySQL 5](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.wc70t0qomrf9)

[● Create Replication Users 6](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.svypoypw813q)

[Login to MySQL and execute: 6](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.gc1bhosyoqog)

[● Create Replication Users 7](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.x2gyoxpm2o4v)

[Login to MySQL and execute: 7](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.59glghs7fggn)

[On Slave 3(final: 192.168.122.246) 8](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.i7p1v74jbt5e)

[● Create Replication Users 8](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.nfk8y8l6wtvg)

[Login to MySQL and execute: 8](https://docs.google.com/document/d/11DBP8xFN74cuVmyl-IZKa-kXyws9_lplir9WU5iz2fM/edit?tab=t.0#heading=h.qo5y5u4bxlza)

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

## Introduction

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdIfrPpnwA-JtglLfVTSz9RkkCPv6ccxPzveAviz5cYNnyErIrRvtR7uy6JJJGufa0ACvVkFRKoq09t8Ar18OediTNSmxCVwRMLZBrfLDnfSUpnm2J8IIFlQk_ccOwMWgmQuoY08g?key=USrM5A1saFdaXqWQYDgLQNhk)

MySQL replication is a process that allows data from one MySQL database server (the primary) to be copied automatically to one or more secondary servers (replicas). This setup is commonly used for load balancing, backup, or data redundancy.

## Servers

| aman: 192.168.1.68 (Master)first-vm: 192.168.122.37 (Slave 1)new: 192.168.122.111 (Slave 2)final: 192.168.122.246 (Slave 3) |
| --- |

## Installation on All Servers

Update package lists:

  

| sudo apt update |
| --- |

  

Install MySQL Server:

  

| sudo apt install mysql-server |
| --- |

  

Start MySQL service:

  

| sudo systemctl start mysql.service |
| --- |

  

Status MySQL service:

  

| sudo systemctl status mysql.service |
| --- |

  
  
  
  
  
  
  

## Master Server (aman: 192.168.1.68)

Allow Incoming Connections

sudo ufw allow from 192.168.122.37 to any port 3306

sudo ufw allow from 192.168.122.111 to any port 3306

  

### Configure MySQL

Edit the configuration file:

| sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf |
| --- |

  

Add the following under \[mysqld\]:

| [mysqld]user        = mysqlbind-address        = 0.0.0.0mysqlx-bind-address = 127.0.0.1key_buffer_size     = 16Mmyisam-recover-options  = BACKUPlog_error = /var/log/mysql/error.logserver-id          = 1log_bin                    = /var/log/mysql/mysql-bin.logenforce_gtid_consistency = ONlog_slave_updates = ONbinlog_expire_logs_seconds = 2592000max_binlog_size   = 100M |
| --- |

  
  

Restart MySQL service:

  

| sudo systemctl restart mysql.service |
| --- |

  

### Create Replication Users

Login to MySQL and execute:

| sudo mysql;CREATE USER 'replica'@'192.168.122.37' IDENTIFIED BY 'aman@123';GRANT REPLICATION SLAVE ON *.* TO 'replica'@'192.168.122.37';CREATE USER 'replica'@'192.168.122.111' IDENTIFIED BY 'aman@123';GRANT REPLICATION SLAVE ON *.* TO 'replica'@'192.168.122.111';FLUSH PRIVILEGES;SHOW MASTER STATUS; |
| --- |

## Slave 1 (first-vm: 192.168.122.37)

### Configure MySQL

Edit the configuration file:

| sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf |
| --- |

  

Add the following under \[mysqld\]:

| [mysqld]user        = mysqlbind-address        = 0.0.0.0mysqlx-bind-address = 127.0.0.1key_buffer_size     = 16Mmyisam-recover-options  = BACKUPlog_error = /var/log/mysql/error.logserver-id          = 2log_bin                    = /var/log/mysql/mysql-bin.logmax_binlog_size   = 100M |
| --- |

  

*   Restart MySQL service:
    

| sudo systemctl restart mysql.service |
| --- |

### Login to MySQL and execute:

| sudo mysqlCHANGE MASTER TOMASTER_HOST='192.168.1.68',MASTER_USER='replica',MASTER_PASSWORD='aman@123',MASTER_LOG_FILE='mysql-bin.000002',MASTER_LOG_POS=1937;START SLAVE;SHOW SLAVE STATUS\G; |
| --- |

  
  

| show slave status\G*************************** 1. row ***************************          Slave_IO_State: Waiting for source to send event              Master_Host: 192.168.1.68              Master_User: replica              Master_Port: 3306            Connect_Retry: 60          Master_Log_File: mysql-bin.000018      Read_Master_Log_Pos: 197          Relay_Log_File: ldap-relay-bin.000002            Relay_Log_Pos: 326    Relay_Master_Log_File: mysql-bin.000018        Slave_IO_Running: Yes        Slave_SQL_Running: Yes          Replicate_Do_DB:      Replicate_Ignore_DB:      Replicate_Do_Table:  Replicate_Ignore_Table:  Replicate_Wild_Do_Table:  Replicate_Wild_Ignore_Table:              Last_Errno: 0              Last_Error:            Skip_Counter: 0      Exec_Master_Log_Pos: 197          Relay_Log_Space: 535          Until_Condition: None          Until_Log_File:            Until_Log_Pos: 0      Master_SSL_Allowed: No      Master_SSL_CA_File:      Master_SSL_CA_Path:          Master_SSL_Cert:        Master_SSL_Cipher:          Master_SSL_Key:    Seconds_Behind_Master: 0Master_SSL_Verify_Server_Cert: No            Last_IO_Errno: 0            Last_IO_Error:          Last_SQL_Errno: 0          Last_SQL_Error:  Replicate_Ignore_Server_Ids:        Master_Server_Id: 1              Master_UUID: cb8a5c55-bdd7-11ef-82f0-e83935559328        Master_Info_File: mysql.slave_master_info                SQL_Delay: 0      SQL_Remaining_Delay: NULL  Slave_SQL_Running_State: Replica has read all relay log; waiting for more updates      Master_Retry_Count: 86400 |
| --- |

  
  
  
  
  

*   ### Create Replication Users
    

### Login to MySQL and execute:

| sudo mysqlCREATE USER 'replica'@'192.168.122.246' IDENTIFIED BY 'aman@123';GRANT REPLICATION SLAVE ON *.* TO 'replica'@'192.168.122.246';FLUSH PRIVILEGES;SHOW MASTER STATUS; |
| --- |

  
  
  
  
  
  

## Slave 2(new: 192.168.122.111)

### Configure MySQL

Edit the configuration file:

| sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf |
| --- |

  

Add the following under \[mysqld\]:

| [mysqld]user        = mysqlbind-address        = 0.0.0.0mysqlx-bind-address = 127.0.0.1key_buffer_size     = 16Mmyisam-recover-options  = BACKUPlog_error = /var/log/mysql/error.logserver-id          = 3log_bin                    = /var/log/mysql/mysql-bin.logmax_binlog_size   = 100M |
| --- |

  

*   Restart MySQL service:
    

| sudo systemctl restart mysql.service |
| --- |

  

*   ### Create Replication Users
    

### Login to MySQL and execute:

  

| Sudo mysqlCHANGE MASTER TOMASTER_HOST='192.168.1.68',MASTER_USER='replica',MASTER_PASSWORD='aman@123',MASTER_LOG_FILE='mysql-bin.000002',MASTER_LOG_POS=1937;START SLAVE;SHOW SLAVE STATUS\G; |
| --- |

  
  
  

| show slave status\G*************************** 1. row ***************************          Slave_IO_State: Waiting for source to send event              Master_Host: 192.168.1.68              Master_User: replica              Master_Port: 3306            Connect_Retry: 60          Master_Log_File: mysql-bin.000018      Read_Master_Log_Pos: 197          Relay_Log_File: ldap-relay-bin.000002            Relay_Log_Pos: 326    Relay_Master_Log_File: mysql-bin.000018        Slave_IO_Running: Yes        Slave_SQL_Running: Yes          Replicate_Do_DB:      Replicate_Ignore_DB:      Replicate_Do_Table:  Replicate_Ignore_Table:  Replicate_Wild_Do_Table:  Replicate_Wild_Ignore_Table:              Last_Errno: 0              Last_Error:            Skip_Counter: 0      Exec_Master_Log_Pos: 197          Relay_Log_Space: 535          Until_Condition: None          Until_Log_File:            Until_Log_Pos: 0      Master_SSL_Allowed: No      Master_SSL_CA_File:      Master_SSL_CA_Path:          Master_SSL_Cert:        Master_SSL_Cipher:          Master_SSL_Key:    Seconds_Behind_Master: 0Master_SSL_Verify_Server_Cert: No            Last_IO_Errno: 0            Last_IO_Error:          Last_SQL_Errno: 0          Last_SQL_Error:  Replicate_Ignore_Server_Ids:        Master_Server_Id: 1              Master_UUID: cb8a5c55-bdd7-11ef-82f0-e83935559328        Master_Info_File: mysql.slave_master_info                SQL_Delay: 0      SQL_Remaining_Delay: NULL  Slave_SQL_Running_State: Replica has read all relay log; waiting for more updates      Master_Retry_Count: 86400 |
| --- |

  

*   ### Create Replication Users
    

### Login to MySQL and execute:

| sudo mysqlCREATE USER 'replica'@'192.168.122.246' IDENTIFIED BY 'aman@123';GRANT REPLICATION SLAVE ON *.* TO 'replica'@'192.168.122.246';FLUSH PRIVILEGES;SHOW MASTER STATUS; |
| --- |

  
  
  
  
  

## On Slave 3(final: 192.168.122.246)

### Configure MySQL

Edit the configuration file:

| sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf |
| --- |

  

Add the following under \[mysqld\]:

| [mysqld]user        = mysqlbind-address        = 0.0.0.0mysqlx-bind-address = 127.0.0.1key_buffer_size     = 16Mmyisam-recover-options  = BACKUPlog_error = /var/log/mysql/error.logserver-id          = 3log_bin                    = /var/log/mysql/mysql-bin.logrelay_log=relay-binslave-skip-errors=1062,1032,1007,1008max_binlog_size   = 100M |
| --- |

  

*   Restart MySQL service:
    

| sudo systemctl restart mysql.service |
| --- |

  

*   ### Create Replication Users
    

### Login to MySQL and execute:

  

| Sudo mysqlCHANGE MASTER TOMASTER_HOST='192.168.122.37',MASTER_USER='replica',MASTER_PASSWORD='admin',MASTER_LOG_FILE='mysql-bin.000008',MASTER_LOG_POS=726FOR CHANNEL 'master1';CHANGE MASTER TOMASTER_HOST='192.168.122.111',MASTER_USER='replica',MASTER_PASSWORD='admin',MASTER_LOG_FILE='mysql-bin.000003',MASTER_LOG_POS=4850FOR CHANNEL 'master2';START SLAVE FOR CHANNEL 'master1';START SLAVE FOR CHANNEL 'master2';SHOW SLAVE STATUS\G; |
| --- |

  
  

| SHOW SLAVE STATUS FOR CHANNEL 'master1'\G*************************** 1. row ***************************          Slave_IO_State: Waiting for source to send event              Master_Host: 192.168.122.37              Master_User: replica              Master_Port: 3306            Connect_Retry: 60          Master_Log_File: mysql-bin.000015      Read_Master_Log_Pos: 157          Relay_Log_File: relay-bin-master1.000026            Relay_Log_Pos: 373    Relay_Master_Log_File: mysql-bin.000015        Slave_IO_Running: Yes        Slave_SQL_Running: Yes          Replicate_Do_DB:      Replicate_Ignore_DB:      Replicate_Do_Table:  Replicate_Ignore_Table:  Replicate_Wild_Do_Table:  Replicate_Wild_Ignore_Table:              Last_Errno: 0              Last_Error:            Skip_Counter: 0      Exec_Master_Log_Pos: 157          Relay_Log_Space: 754          Until_Condition: None          Until_Log_File:            Until_Log_Pos: 0      Master_SSL_Allowed: No      Master_SSL_CA_File:      Master_SSL_CA_Path:          Master_SSL_Cert:        Master_SSL_Cipher:          Master_SSL_Key:    Seconds_Behind_Master: 0Master_SSL_Verify_Server_Cert: No            Last_IO_Errno: 0            Last_IO_Error:          Last_SQL_Errno: 0          Last_SQL_Error:  Replicate_Ignore_Server_Ids:        Master_Server_Id: 2              Master_UUID: 1a4ea144-bdd8-11ef-8a4b-525400da2308        Master_Info_File: mysql.slave_master_info                SQL_Delay: 0      SQL_Remaining_Delay: NULL  Slave_SQL_Running_State: Replica has read all relay log; waiting for more updates      Master_Retry_Count: 86400              Master_Bind:  Last_IO_Error_Timestamp:Last_SQL_Error_Timestamp:          Master_SSL_Crl:      Master_SSL_Crlpath:      Retrieved_Gtid_Set:        Executed_Gtid_Set:            Auto_Position: 0    Replicate_Rewrite_DB:            Channel_Name: master1      Master_TLS_Version:  Master_public_key_path:    Get_master_public_key: 0        Network_Namespace:1 row in set, 1 warning (0.00 sec) |
| --- |

  

| SHOW SLAVE STATUS FOR CHANNEL 'master2'\G*************************** 1. row ***************************          Slave_IO_State: Waiting for source to send event              Master_Host: 192.168.122.111              Master_User: replica              Master_Port: 3306            Connect_Retry: 60          Master_Log_File: mysql-bin.000007      Read_Master_Log_Pos: 2035          Relay_Log_File: relay-bin-master2.000010            Relay_Log_Pos: 894    Relay_Master_Log_File: mysql-bin.000007        Slave_IO_Running: Yes        Slave_SQL_Running: Yes          Replicate_Do_DB:      Replicate_Ignore_DB:      Replicate_Do_Table:  Replicate_Ignore_Table:  Replicate_Wild_Do_Table:  Replicate_Wild_Ignore_Table:              Last_Errno: 0              Last_Error:            Skip_Counter: 0      Exec_Master_Log_Pos: 2035          Relay_Log_Space: 2019          Until_Condition: None          Until_Log_File:            Until_Log_Pos: 0      Master_SSL_Allowed: No      Master_SSL_CA_File:      Master_SSL_CA_Path:          Master_SSL_Cert:        Master_SSL_Cipher:          Master_SSL_Key:    Seconds_Behind_Master: 0Master_SSL_Verify_Server_Cert: No            Last_IO_Errno: 0            Last_IO_Error:          Last_SQL_Errno: 0          Last_SQL_Error:  Replicate_Ignore_Server_Ids:        Master_Server_Id: 3              Master_UUID: 4e521ae4-bdf0-11ef-be8b-525400f21482        Master_Info_File: mysql.slave_master_info                SQL_Delay: 0      SQL_Remaining_Delay: NULL  Slave_SQL_Running_State: Replica has read all relay log; waiting for more updates      Master_Retry_Count: 86400              Master_Bind:  Last_IO_Error_Timestamp:Last_SQL_Error_Timestamp:          Master_SSL_Crl:      Master_SSL_Crlpath:      Retrieved_Gtid_Set:        Executed_Gtid_Set:            Auto_Position: 0    Replicate_Rewrite_DB:            Channel_Name: master2      Master_TLS_Version:  Master_public_key_path:    Get_master_public_key: 0        Network_Namespace:1 row in set, 1 warning (0.00 sec) |
| --- |

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

### Explanation:

1.  Master Server (aman): This is the primary MySQL server, where data is written. It's configured to allow connections from the slave servers and is the source of the replication.
    
2.  Slave Servers (first-vm, new, final): These are the secondary servers that receive replicated data from the master. Each one is configured to connect to the master and replicate data.
    
3.  Connections: The diagram shows the replication flow, with arrows indicating how the master replicates data to each slave. Additionally, it shows replication between slave servers, which is typical for a multi-tier replication setup.
    

  

## Conclusion

MySQL replication setup described provides a robust and scalable solution for ensuring data redundancy, load balancing, and high availability across multiple servers. By configuring a master server along with multiple slave servers, this setup allows for the automatic synchronization of data across all nodes, ensuring consistency and reliability. The detailed process for installing MySQL, configuring replication settings, creating replication users, and verifying the replication status ensures that the entire environment is properly configured and optimized. This approach enhances the performance and reliability of database systems, making them suitable for production environments with high data demands and failover requirements.
