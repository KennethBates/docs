Iindex.md -Done

## move-the-database-and-server.md	
- Follow the steps as outlined below to move the database
- Move the 3 folders (Packages, Task Logs and Artifacts) from the old server to the new server
- Restart your server to index the files which were moved.

The database stores the locations for these directories. After you connect to the database, your settings will be the same as they were in your original server. You can change the locations for these directories, but we recommend first moving the directories themselves, and then updating the location setting in which they are looked for.

## move-the-database.md
- We recommend using the Backup option in your current database, then the Import option on the destination server.
- Keep in mind that after any change like this, you will also need to update your OctopusServer.config file to match the new destination.


This page outlines our recommended steps to move your SQL database to another server. Deployments and events are continually being written to the database, so to ensure all of your data is migrated, follow these steps.

## Process
1. Place your Octopus instance into Maintenance Mode and stop the service when all deployments have completed.
2. Ensure you have saved a copy of your [master key](https://octopus.com/docs/reference/security-and-encryption#Securityandencryption-YourMasterKey).
3. Take a backup of your Octopus database.
4. Restore the database on your new server.
5. Create a new Octopus instance using the same Octopus version as your original instance. You can find any version in our [previous releases](https://octopus.com/downloads/previous) page.
6. During the installation of your new instance, select the database you restored. It will prompt for the master key.
7. Log in to your new server and disable Maintenance Mode.

:::hint
When running the Octopus Deploy service as a Local System account, Windows Authentication can be used only if the SQL server instance is hosted on the same machine. To host SQL Server remotely, use SQL Server Authentication, or run the Octopus Deploy service as a custom account.
:::
-
-
-

move-the-home-directory.md
-
-
-
-
-

move-the-server.md
-
-
-
-
-

replicating-your-octopus-instance-in-a-test-environment.md
-
-
-
-
-
