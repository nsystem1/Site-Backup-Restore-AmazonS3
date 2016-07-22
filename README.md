# Site Backup and Restore - Amazon S3 Bucket
---
Taking backup of a huge site and database to amazon s3 bucket by manually or setting cron job to perform regular backups. View the **`docs/screenshots`** for steps of process.

##### How to?

+ Installation & Configuration
+ Taking backup only once.
+ Setting cron for Automated Backups
+ Restoration Process

**Installation & Configuration:**

1. Upload files to directory outside to the actual backup folder and make sure it is not publicly accessible.
2. Create config file inside “config” folder. Follow & copy example ini file.

**Taking backup only once:**

Just run the command  in terminal/ ssh. Follow the instructions show in the terminal, backups will be copied to s3 after that.

    php PATH_TO_SCRIPT/backup-cron.php start:true config:example

**Setting cron for Automated Backups:**

1. Make sure to have active config file inside config folder.
2. Add cron command `Eg. “php PATH_TO_SCRIPT/backup-cron.php start:true config:example”`
3. Only one backup process will be done at a time, hence a lock file is created. Lock file will be removed after performing backup process. If script is manually terminated or thread terminated abnormally then make sure that in “backupProcess.lock” file doesn’t exist in script folder. If exist remove it to retry the operation again.
4. If config `IS_DO_DATABASE_BACKUP` is set to `true`, database also be taken backup.
5. Check log file in logs if it requires some information about how process done.

**Restoration Process:**

1. Make sure to have active config file inside config folder.
2. Run command from console
`Eg. “php PATH_TO_SCRIPT/restoreConsole.php start:true config:example”`
3. Only one restoration process will be done at a time, hence a lock file is created. Lock file will be removed after performing restoration process. If script is manually terminated or thread terminated abnormally then make sure that in “restoreProcess.lock” file doesn’t exist in script folder. If exist remove it.
4. If config has defined values to `RESTORATION_CONFIG` then it will be selected and shown by default. Else configs will be asked in the terminal.
5. Check log file in logs if it required.

**Screen Shots:**

![Config](https://raw.githubusercontent.com/vijaynaidu/Site-Backup-Restore-AmazonS3/master/docs/screenshots/1.png)

![Config editor](https://raw.githubusercontent.com/vijaynaidu/Site-Backup-Restore-AmazonS3/master/docs/screenshots/2.png)

![Creating folder for restoration](https://raw.githubusercontent.com/vijaynaidu/Site-Backup-Restore-AmazonS3/master/docs/screenshots/3.png)

![Aws S3 Console](https://raw.githubusercontent.com/vijaynaidu/Site-Backup-Restore-AmazonS3/master/docs/screenshots/4.png)

![Taking backup from ssh/ terminal](https://raw.githubusercontent.com/vijaynaidu/Site-Backup-Restore-AmazonS3/master/docs/screenshots/5.png)

![Aws S3 Console with backup files](https://raw.githubusercontent.com/vijaynaidu/Site-Backup-Restore-AmazonS3/master/docs/screenshots/6.png)

![Restoration of files, database from ssh/ terminal](https://raw.githubusercontent.com/vijaynaidu/Site-Backup-Restore-AmazonS3/master/docs/screenshots/7.png)

