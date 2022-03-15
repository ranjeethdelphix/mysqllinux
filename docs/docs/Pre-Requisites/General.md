# General

Given below are the general pre-requisites for MySQL virtualization.

### Environments
For MySQL virtualization, Delphix requies only Staging and Target Hosts to be added as environments.

Refer to [Delphix Docs](https://docs.delphix.com/docs/configuration/performance-analytics-management/target-host-os-and-database-configuration-options)
for configuration best practices.

##### Staging Host/Environment
   The MySQL plugin is a "Staged" plugin - which means that in order to create a dSource, Delphix requires a staging environment.
   This environment must have MySQL binaries installed and the version of MySQL on Staging host must be same as the Source host.

##### Target Host/Environment
 Target host is a the environment where the virtual copies of the databases are hosted.
 It is a host with MySQL binaries installed and Delphix creates virtual databases on this host. The version of MySQL must be the same as Source host.

 Even though a stage and target host can be same environment, it is strongly recommended to maintain staging and target hosts separate considering the performance challenges arising from shared resource utilization.

### Storage
- Staging & Target host to hold delphix toolkit directory. Please refer to the link for toolkit directory requirements
https://docs.delphix.com/docs/datasets/unstructured-files-and-app-data/unstructured-files-environment-requirements/unstructured-files-on-unix-environments/requirements-for-unix-environments

- If Delphix is managing backups, the Staging Host must have enough storage space in user specified backup location to host source database backup files.

### MySQL Version
- MySQL Binary version on Staging and Target must match the version on the source database(s)
