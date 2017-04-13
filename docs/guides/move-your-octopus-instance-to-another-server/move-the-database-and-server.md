
## move-the-database-and-server.md	

Below are instructions on how to move your Octopus server and SQL Database.

1. Place your Octopus instance into Maintenance Mode and stop the service when all deployments have completed. You can stop the service via the Octopus Manager, or via the command line using the following command.
`Octopus.Server.exe service --stop`
2. Ensure you have saved a copy of your [master key](https://octopus.com/docs/reference/security-and-encryption#Securityandencryption-YourMasterKey).
3. Take a backup of your Octopus database.
4. Restore the database on your new server.
5. Create a new Octopus instance using the same Octopus version as your original instance. You can find an older version and download the MSI in our [previous releases](https://octopus.com/downloads/previous) page.
6. During the installation of your new instance, select the database you restored. It will prompt for the master key.
7. Copy the following directories from your original server to the new server (each of these folders are located in C:\Octopus in standard installations).
   - Artifacts
   - Task Logs
   - Packages
      - This folder only needs to be moved if using the built-in package repository. External feed details are stored in the database, and they will connect automatically.
8. Finally, restart your new Octopus instance to index the packages. You can restart either in your Octopus Manager, or via the command line with the following command.
```
Octopus.Server.exe service --stop
Octopus.Server.exe service --start
```

The database stores the locations for these directories. After you connect to the database, your settings will be the same as they were in your original server. You can change the locations for these directories, but we recommend first moving the directories themselves, and then pointing to the new location. This process is outlined in the [moving the home directory](/docs/getting-started.md) page.

- [Moving the database](/docs/move-the-database.md)
- [Moving the server](/docs/move-the-server.md)
- [Moving the home directory](/docs/getting-started.md)
- [Replicating your Octopus instance in a test environment](/docs/replicating-your-octopus-instance-in-a-test-environment.md)
