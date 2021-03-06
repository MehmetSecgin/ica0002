# Backup restoration process for MySql and InfluxDB

## MySql
### Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

### Restore MySQL data from the backup:


    sudo -u backup duplicity --no-encryption --force restore rsync://Scentryum@backup.snackdrivein.io//home/Scentryum/mysql/ /home/backup/restore/

    sudo -i

    mysql agama < /home/backup/restore/agama.sql

### Verify the restoration

    sudo mysql -e 'SELECT * FROM agama.item'

## InfluxDB

### Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

### Restore InfluxDB data from the backup:

    sudo -u backup duplicity --no-encryption --force restore rsync://Scentryum@backup.snackdrivein.io//home/Scentryum/influxdb/ /home/backup/restore/
    sudo service telegraf stop
    sudo influx -execute 'DROP DATABASE telegraf'
    sudo influxd restore -portable -database telegraf /home/backup/influxdb

### After you have verified that backup was restore successfully, run

    ansible-playbook infra.yaml
