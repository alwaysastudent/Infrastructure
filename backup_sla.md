Backup SLA

Services served by this infrastracutre are relied on databases.
Therefore, backups should focus on databases.
The following is a summary of the infrastracture architecture:

- Nginx as web Server.
- Agama as web Application.
- MySql Database.
- Bind is the main DNS server in which our services are configured according to.
- Prometheus works with exporters to deliver metrics of our services.
- Telegraf works with Influxdb for syslog.
- Grafana has Prometheus and Influxdb as a datasource.

Coverage: Included Services
- MySQL: Database Dump, will have our wp data.
- InfluxDb: Database Dump.
- Grafana: Database and Configuration (JSON Format/grafana.db).

Storage
- Backup scheme should follow the 3-2-1 rule.
two onsite, each in different backup server(s)
One in a cloud option, or an offsite datacenter.

Coverage: Excluded Services
- Haproxy: Provisioned with Ansible.
- Telegraf: everything we need is already in influxdb.
- Prometheus: Provisioned with Ansible along with exporters.
- Bind: Provisioned with Ansible.

RTO
- 8 hours maximum of downtime is the way to go for our highly available services.

RPO
- We can only afford 8 hours of RTO, therefore, we should have just 12 hours of RPO to keep data loss at a minimum.

Frequency
- Datadump: every day at 23:00
- Full backups: every day at 23:10
- Incremental backup: every week day from monday to saturday at 23:10
- Drop backup data after 30 days.

Versioning
- Due to our frequency, different versions of the backups should be present.

Retention
- Backups with a shelf-life of older than 30 days are deemed to be unusable and thus deleted.

Usability
- Verifying the integrity of our backups should be done weekly.