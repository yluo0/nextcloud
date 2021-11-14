# nextcloud

Configure Nextcloud on Opensuse

****** add 2 lines in etc/appache2/default-server.conf ****
Include /etc/apache2/conf.d/*.conf
Include /etc/apache2/vhosts.d/*.conf


By default, Apache in openSUSE Leap is prepared for one configuration file per virtual host in /etc/apache2/vhosts.d/. All files in this directory with the extension .conf are automatically included to the configuration. A basic template for a virtual host is provided in this directory (vhost.template or vhost-ssl.template for a virtual host with SSL support).
