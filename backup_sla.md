# Backup services SLA

## Backup coverage

Backup service covers only the next services:

- Database services - **MySQL, InfluxDB**

## RPO

Recovery point objective for:

- **MySQL** and **InfluxDB** equals **24 Hours** since system makes backups once a day.

## Versioning and retention

- **MySQL** and **InfluxDB** backups are retained for  **30 days**. Since we use incremental backuping every day we store a different version, 
so 30 versions in total.

## Usability

Usability of the last **MySQL** and **InfluxDB** backup is regularly checked every **1 weeks/7 days** before new modifications to Ansible repo is done. The test is done on the virtual environment setup, simulating our real infrastructure.

## Restoration criteria

- Backup restoration of the **MySQL** or **InfluxDB** data should be done only if it was detected and confirmed that the stored data was corrupted, modified by the unauthorized 1st/3rd party, stolen or deleted.

## Backup RTO

- Backup service is expected to take maximum of **2 hours** to fully recover all the data.
