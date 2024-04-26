# CTERAChronicleCollector
Portal Usage Report Collector Installation
wget https://github.com/keywork/CTERAChronicleCollector/raw/main/portal-usage-collector.zip
1. Place the portal-usage-collector binary in /usr/local/ctera/bin/
2. As the root user, run: portal-usage-collector --setup
3. Modify the contents of /home/ctera/.env to match your SDK login details using a R/W Admin user.
4. Check that the crontabs were properly added:
   
	su - ctera
	crontab -l

You should see:

	[ctera@portal ~]$ crontab -l
	* * * * * /usr/local/ctera/bin/portal-usage-collector # Generates reports if older than 7 Days
	* * */7 * * /usr/local/ctera/bin/portal-usage-collector --collect # Store portal reports in $tomcatlogs/usage_report

This will create a weekly ZIP file in $tomcatlogs/usage_report that can be collected by the using 'portal-dump.sh -l'
