# CTERAChronicleCollector
Portal Usage Report Collector Installation


Place the portal-usage-collector binary in /usr/local/ctera/bin/ of any CTERA portal server. As the root user, run:
	
 	cd /usr/local/ctera/bin/
	wget https://github.com/keywork/CTERAChronicleCollector/raw/main/portal-usage.zip
	unzip portal-usage.zip
	rm -f portal-usage.zip
	chmod +x portal-usage-collector
	portal-usage-collector --setup

Modify the contents of /home/ctera/.env to match your SDK login details using a R/W Admin user.
Check that the crontabs were properly added:

You should see:
	
	[root@portal ~]# su - ctera
	[ctera@portal ~]$ crontab -l
	0 18 * * * /usr/local/ctera/bin/portal-usage-collector # Generates reports if older than 7 Days
	0 6 1 * * /usr/local/ctera/bin/portal-usage-collector --collect # Store portal reports in $tomcatlogs/usage_report

This will create a weekly ZIP file in $tomcatlogs/usage_report that can be collected by the using 'portal-dump.sh -l'
