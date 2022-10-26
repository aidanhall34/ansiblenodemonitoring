# ansiblemonitoring
### For monitoring servers with Prometheus and Grafana
### Deployed with ansible

Blog post: https://blog.ah34.net/posts/grafana-prometheus-loki-and-ansible/
Youtube video: https://www.youtube.com/watch?v=1xpxiwCIwS8


To run the playbook, update the values in ```inventories/group_vars/ubuntu.yml```. Ensure that the SNMP_exporter, Promethues and other agent / server configs will work in your environment.

Then run:
```bash
# Run this on the monitoring server
ansible-playbook playbooks/deploy_monitoring.yml  -i inventories/production/ --tags server --limit '<monitoring server>'
# Run this on all machines except for the monitoring server
ansible-playbook playbooks/deploy_monitoring.yml  -i inventories/production/ --tags agent --limit '<agent server group>:!<monitoring server>'
```