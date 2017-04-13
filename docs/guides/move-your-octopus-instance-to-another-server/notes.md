Iindex.md -Done

move-the-database-and-server.md	
-
-
-
-

## move-the-database.md
- We recommend using the Backup option in your current database, then the Import option on the destination server.
- Keep in mind that after any change like this, you will also need to update your OctopusServer.config file to match the new destination.


You may just want to move your SQL database to another server. Because deployments and events are written to the database as they occur, we would recommend following a step-by-step process to ensure nothing is lost in the database move.

## Process
1. Place your Octopus instance into Maintenance Mode and stop the service when all deployments have completed.
2. Take note of your master key
3. Take a backup of your Octopus database.
4. Restore the database on your new server.
5. Create a new Octopus instance. Use the same Octopus version as your existing instance.
6. During the installation of your new instance, select the restored database. It will prompt for the master key.

:::hint
When running the Octopus Deploy service as a Local System account, windows Authentication can be used only if the SQL server instance is hosted on the same machine. To host SQL Server remotely, use SQL Server Authentication, or run the Octopus Deploy service as a custom account.
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
