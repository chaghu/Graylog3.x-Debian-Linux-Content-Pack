# Graylog3.x-Debian-Linux-Content-Pack

This content pack helps you set up an input(to receive your linux logs on port 5140), accompanied with grok pattern extractors to extract important fields on linux messages, geoIP pipeline rules to pinpoint the exact location of remote host IPs and linux dashboards. 


# Graylog Version

The content pack is tested on Graylog3.1 version.


# Pipeline Rules

For the pipeline rules to be effective please follow the following steps:

1.  When you log into graylog web interface, navigate to *System/Configurations*

2.  Re-order the *Message Processors Configuration* section as follows:
      *Message Filter Chain -> GeoIP Resolver -> Pipeline Processor*
The order of message processors may have a significant impact on how your messages get processed as described in the follwoing graylog     documentation: https://docs.graylog.org/en/3.1/pages/pipelines/stream_connections.html#message-processor-ordering

3. Activate GeoIP Resolver in the *Message Processors Configuration* section by checking the box

4. Enable the Geo-location Processor plugin under the *Geo-location Processor* section

5. Upload geo-location information database on the path indicated under the *Geo-location Processor* section, i.e. on the backend of server running Graylog. You can find Free Geolocation Database on the following site: https://dev.maxmind.com/geoip/geoip2/geolite2/

6. Then restart the graylog service for changes to take place by running the following command if you are running graylog on a linux environment:
 
     *$ sudo systemctl restart graylog-server.service*

6. Congratulations, your graylog pipeline rule is now working!

#Dashboards

To get results for the *User Linux Commandline* widget, you need to enable commandline auditing on your linux machine as described here: https://confluence.atlassian.com/confkb/how-to-enable-command-line-audit-logging-in-linux-956166545.html
