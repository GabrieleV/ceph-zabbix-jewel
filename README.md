Zabbix-ceph-jewel

Check items of a ceph cluster and notify health problems.

Based on https://github.com/zphj1987/ceph-zabbix-jewel.


##installation

    cp etc/zabbix/zabbix_agentd.d/zabbix-ceph-jewel.conf  /etc/zabbix/zabbix_agentd.d
    systemctl restart zabbix-agent

    mkdir -p /etc/zabbix/scripts
    cp etc/zabbix/scripts/ceph-status.py /etc/zabbix/scripts/
    chmod +x /etc/zabbix/scripts/ceph-status.py

    cp etc/sudoers.d/zabbix-ceph-jewel /etc/sudoers.d/zabbix-ceph-jewel

Test from agent machine:
    sudo -u zabbix /usr/bin/sudo /etc/zabbix/scripts/ceph-status.py health

Test from server/proxy
    zabbix_get -s 1.2.3.4  -k ceph.health

##template

Load the XML template into Zabbix
