# nextcloud

Configure Nextcloud on Opensuse

****** add 2 lines in etc/appache2/default-server.conf ****
Include /etc/apache2/conf.d/*.conf
Include /etc/apache2/vhosts.d/*.conf


By default, Apache in openSUSE Leap is prepared for one configuration file per virtual host in /etc/apache2/vhosts.d/. All files in this directory with the extension .conf are automatically included to the configuration. A basic template for a virtual host is provided in this directory (vhost.template or vhost-ssl.template for a virtual host with SSL support).
cp & rename :/etc/apache2/vhosts.d/vhost-ssl.template to /etc/apache2/vhosts.d/*.conf 
edit 

<VirtualHost _default_:443>

        #  General setup for the virtual host
        DocumentRoot "/srv/www/htdocs"
        ServerName localhost:443
        ServerAdmin ericjingluo@qq.com
        ErrorLog /var/log/apache2/error_log
        TransferLog /var/log/apache2/access_log

        #   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
        SSLEngine on

        #   OCSP Stapling:
        #   Enable/Disable OCSP for this virtual host.
        SSLUseStapling  on

        #   You can use per vhost certificates if SNI is supported.
        SSLCertificateFile /etc/apache2/ssl.crt/server.crt
        SSLCertificateKeyFile /etc/apache2/ssl.key/server.key
        #SSLCertificateChainFile /etc/apache2/ssl.crt/vhost-example-chain.crt

        #   Per-Server Logging:
        #   The home of a custom SSL log file. Use this when you want a
        #   compact non-error SSL logfile on a virtual host basis.
        CustomLog /var/log/apache2/ssl_request_log   ssl_combined
        <IfModule mod_headers.c>
         Header always set Strict-Transport-Security "max-age=15552000; includeSubDomains"
        </IfModule>

</VirtualHost>
