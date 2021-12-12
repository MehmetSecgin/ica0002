# Backup services SLA

## Backup coverage

Backup service covers only the next services:

- Database services - **MySQL, InfluxDB**
- Ansible repository

## RPO

Recovery point objective for:

- **MySQL** equals **28 days**.
- **InfluxDB** equals **28 days**.
- **Ansible repository** equals **7 days**.

## Versioning and retention

- **MySQL** and **InfluxDB** backups are retained for **56 days**, only 2 versions can be stored at the same time.
- **Ansible repository** backups are retained for **14 days**, only 2 versions should be stored at the same time.

## Usability

Usability of the last **MySQL**, **InfluxDB**, **Grafana** and **Ansible repository** backup is regularly checked every **1 weeks/7 days** before new modifications to Ansible repository and Grafana configuration is done. The test is done on the virtual environment setup, simulating our real infrastructure.

## Restoration criteria

- Backup restoration of the **MySQL** or **InfluxDB** data should be done only if it was detected and confirmed that the stored data was corrupted, modified by the unauthorized 1st/3rd party, stolen or deleted.
- **Ansible repository** backup should only be used if the reconfiguration of services is required, and original GitHub based repository is unavailable, or the process of acquiring and using a backup copy is faster than acquiring and using GitHub's copy.

## Backup RTO

- Backup service is expected to take maximum of **2 hours** to fully recover all the data.
