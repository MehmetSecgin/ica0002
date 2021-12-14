# Backup restoration process for MySql and InfluxDB

## MySql
### Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

### Restore MySQL data from the backup:

    duplicity --no-encryption restore rsync://<backup_user>@<our_domain>//home/<backup_user> /home/backup/restore/

    mysql agama < /home/backup/restore/agama.sql

### Verify the restoration

    mysql -e 'SELECT * FROM agama.item'

## InfluxDB

### Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

### Restore InfluxDB data from the backup:

    service telegraf stop
    influx -execute 'DROP DATABASE telegraf'
    influxd restore -portable -database telegraf /home/backup/influxdb

### After you have verified that backup was restore successfully, run

    ansible-playbook infra.yaml
