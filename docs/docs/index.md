# Overview

MySQL plugin has been developed to ingest and virtualize MySQL data sources using Delphix.

What does MySQL plugin do?
--------------------------
The Delphix MySQL Plugin can virtualize a single instance MySQL database and create
multiple virtual copies as required.

There are two modes of operation of the plugin based on how the MySQL dSource is created
and kept in-sync with source database.

### Replication

In the Replication mode, Delphix uses MySQL's built-in replication technology to keep
the Delphix dSource in-sync with the MySQL source databases.

Creation of the dSource requires a full backup of the source database(s) and there are
two options to providing this backup.

1. Delphix Managed Backup

    In this option, Delphix is provided with the required information to take
    a full backup of the source database.

2. User Provided Backup

    In this option, user provides Delphix with an existing full backup.
    Delphix initializes the staging database using the full backup and configures the
   staging database as a replicated slave of the source database.
    MySQL Replication keeps the data in the staging database in-sync with the source.

    Here is a link to MySQL documentation on how to trigger mysqldump: https://dev.mysql.com/doc/refman/5.7/en/mysqldump-tips.html

### Manual Ingestion
In the Manual Ingestion mode, the data in Delphix dSource is managed manually by the end users.
Delphix creates a seed MySQL staging database which can be managed via Delphix.
The end user assumes the responsibility of keeping the data in the staging
database in-sync with the source database.

There are two ways how end user may choose to keep data in-sync with source:
  1.  Setup MySQL replication
      After initial mysqldump restore on staging MySQL server, setup master / slave replication between source and stage servers. Please refer to MySQL documentation on how to setup replication
      https://dev.mysql.com/doc/refman/5.7/en/replication.html

  2.  Schedule periodic full backup restore
      After initial mysqldump restore on staging MySQL server, arrange for periodic ingestions of full mysqldump from source to stage. This method of synchronization does not provide point in time refresh service. The snapshots available for the refresh will be in-line with the backups ingested

    Here is a link to MySQL documentation on how to trigger mysqldump: https://dev.mysql.com/doc/refman/5.7/en/mysqldump-tips.html

### Network Architecture
Here is the MySQL virtualization network architecture
![Logo](/docs/docs/image/Arch-Diag.png)


Limitations
-----------
Virtual to Physical (V2P): Untested

Enterprise Raw Backup/Restore: Untested

Transparent Data Encryption: Untested

Virtualizing Master / Slave: Strongly recommended to ingest cold backups for Master / Slave databases to avoid data loss / inconsistency   

Where to Start?
--------------
By now, you must have an overall idea of what is possible with the MySQL plugin.
Before you can get started with virtualizing your MySQL databases,
there are some pre-requisites you need to take care of.
Please visit the [Pre-Requisites](/Pre-Requisites/General/index.html) page for more details.
