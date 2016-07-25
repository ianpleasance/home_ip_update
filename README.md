# home_ip_update
Automatic update of iptables/EC2 Security Group to allow access from a remote Internet connection (e.g. your home) with a Dynamic IP address.

This is a set of scripts that I install on servers to allow remote access to firewall-protected servers from a home Internet connection which has a Dynamic IP address.
It supports servers that use IPTables as a firewall, and servers that are behind EC2 Security Groups.

The scripts assume that your home router updates a hostname provided by a Dynamic DNS provider on reconnection. They check this regularly and detect a change, and after a change update firewall configuration accordingly.

Installation and usage

- Create yourself a Dynamic DNS name for your home Internet connection, for example dyndns.org or duckdns.org
- Change your router's configuration to update this dynamic DNS name on each successful connection to the Internet.

- Download repo contents
- Copy fw_* and home_ip_update to /root, chmod 755
- If your servers are using IPTables as a firewall, then install etc/iptables.firewall.rules.var into /etc and add any firewall rules that you need.
- If your servers are using EC2 Security Groups as a firewall, then update fw_update_ec2 to add AWS credentials
- Update the home_ip_update script
- Install the cron.d/home_ip_update into /etc/cron.d or into a crontab entry (running as root)
- Wait for the first run to complete
- Test access from home


