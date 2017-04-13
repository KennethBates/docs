---
title: Moving the database
description: Walkthrough outlining how you can move an Octopus database from one server to another.
position: 0
---

This page outlines our recommended steps to move your SQL database to another server. Deployments and events are continually being written to the database, so to ensure all of your data is migrated, you will want to avoid starting any new deployments, and finish currently running deployments and tasks. The following is our recommended approach to moving your Octopus database while retaining all of your data.

## Step-by-step Process
1. Place your Octopus instance into Maintenance Mode and stop the service when all deployments have completed. You can stop the service via the Octopus Manager, or via the command line using the following command.
`Octopus.Server.exe service --stop`
2. Ensure you have saved a copy of your [master key](https://octopus.com/docs/reference/security-and-encryption#Securityandencryption-YourMasterKey).
3. Take a backup of your Octopus database.
4. Restore the database on your new server.
5. On your original Octopus server, run the following command to update the connection string (where "VALUE" is your connection string. An example connection string looks like `Data Source=MyServerAddress\SQLEXPRESS;Initial Catalog=OctopusDatabase;Integrated Security=True`).

`Octopus.Server.exe configure --storageConnectionString="VALUE"`

6. Ensure the user specified in the connection string has access to the database as a **dbo_owner**. Refer to our [SQL server database requirements](https://octopus.com/docs/installation/installing-octopus/sql-server-database-requirements) documentation page.

:::hint
When running the Octopus Deploy service as a Local System account, Windows Authentication can be used only if the SQL server instance is hosted on the same machine. To host SQL Server remotely, use SQL Server Authentication, or run the Octopus Deploy service as a custom account.
:::

- [Moving the server](/docs/move-the-server.md)
- [Moving the database and server](/docs/move-the-database-and-server.md)
- [Moving the home directory](/docs/getting-started.md)
- [Replicating your Octopus instance in a test environment](/docs/replicating-your-octopus-instance-in-a-test-environment.md)
