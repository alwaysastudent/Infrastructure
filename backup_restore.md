Nginx
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "nginx"
~~~

MySQL
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "mysql"
~~~

AGAMA
-----
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "agama_docker"
~~~
Restore the data from the backup:
backup user:
~~~
duplicity --no-encryption restore rsync://<github_user>@backup.skaldr.io//home/<github_user>/ /home/backup/restore/
mysql agama < /home/backup/restore/agama.sql
~~~

DNS
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "dns_servers"
~~~

Prometheus
---
Install and configure with Ansible:

~~~
ansible-playbook infra.yaml --tags "prometheus"
~~~

Grafana
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "grafana"
~~~
Restore the data from the backup:
backup user:
~~~
duplicity --force --no-encryption restore rsync://anhhungggg@backup.skaldr.io//home/anhhungggg/ /home/backup/restore/
~~~
root user:
~~~
cp -a /home/backup/backup/grafana/* /var/lib/grafana/
~~~



Exporters
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "expt"
~~~

Telegraf
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "telegraf"
~~~

Rsyslog input for telegraf
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "rsyslog"
~~~

Influxdb
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "influxdb"
~~~
Restore the data from the backup:
backup user:
~~~
duplicity --no-encryption restore rsync://<github_user>@backup.skaldr.io//home/<github_user>/ /home/backup/restore/
~~~
root user:
~~~
cp -a /home/backup/restore/influxdb/* /var/lib/influxdb/
~~~

HAproxy
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "haproxy"
~~~

Keepalived
---
Install and configure with Ansible:
~~~
ansible-playbook infra.yaml --tags "keepalived"
~~~

For latest restore point:
---
~~~
su - backup duplicity --force --no-encryption restore rsync://<github_user>@backup.skaldr.io//home/<github_user>/ /home/backup/restore/
~~~
