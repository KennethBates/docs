---
title: Moving the server
description: Walkthrough outlining how you can move an Octopus instance from one server to another.
position: 1
---

You may want to move only the server itself, and continue using your existing database. The following process servers as an outline to help you achieve this.

## Some things to note prior to moving your Octopus instance
- You will need your master key in order for your new Octopus installation to connect to your existing database. You can retrieve and save a copy of the [master key](https://octopus.com/docs/reference/security-and-encryption) in the Octopus Manager.

- Data that is stored in the file system needs to be moved over to the new server. These are your Packages stored in the built-in package repository, your artifacts, and your Task Logs. Instructions on doing this are outlined in the next section.
- Tentacle thumbprints are stored in the database. If you’re using the same database, you won’t need to re-configure your Tentacles.
- [Remote connections](https://msdn.microsoft.com/en-us/library/ms191464.aspx) need to be enabled and configured in SQL server if applicable.  

:::warning
If you are following this guide to move your instance to an upgraded Octopus version, there are important aspects to consider depending on which version you’re upgrading from. Refer to our [upgrading guides](https://octopus.com/docs/administration/upgrading) for applicable information for your scenario.
:::

### Process

1. On your new server, [download and install the MSI](https://octopus.com/downloads).

2. Connect to your existing database in your Octopus Manager using your master key.

3. After your existing database is connected to your new Octopus installation, copy the following directories to your new server (the paths listed are default installation directories):
   - Packages (C:\Octopus\Packages)
   This folder only needs to be moved if using the built-in package repository. External feed details are stored in the database, and they will connect automatically.
   - Artifacts (C:\Octopus\Artifacts)
   - Task Logs (C:\Octopus\TaskLogs)

If you copied the packages folder, you will need to restart your new Octopus instance to index the packages. You can restart either in your Octopus Manager, or via the command line with the following command.
```
Octopus.Server.exe service --stop
Octopus.Server.exe service --start
```
:::info
Octopus 2.6 and older, built-in repository packages were stored in the directory C:\Octopus\OctopusServer\Repository\Packages. If upgrading, you will need to copy the Packages folder to the C:\Octopus\Packages directory.
:::

- [Moving the database](/docs/move-the-database.md)
- [Moving the database and server](/docs/move-the-database-and-server.md)
- [Moving the home directory](/docs/getting-started.md)
- [Replicating your Octopus instance in a test environment](/docs/replicating-your-octopus-instance-in-a-test-environment.md)
