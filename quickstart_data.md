# PREFACE
This guide takes you through the process of installing ownCloud on Red Hat Enterprise Linux. It lists the ownCloud requirements, describes the installation process, and provides basic configuration instructions.

# OWNCLOUD REQUIREMENNTS
Review the server requirements prior to installing the ownCloud server. Install the related software before you install ownCloud.

Information for installing the ownCloud Enterprise Edition or the ownCloud appliance is available in the [ownCloud documentation](https://doc.owncloud.org/server/latest/admin_manual/contents.html).

## Operating System
- Red Hat Enterprise Linux 6.9, 7.3, or 7.4

## Database
- MySQL
- MariaDB 5.5+
- Oracle 11g
- PostgreSQL
- SQLite

## Web Server
- Apache 2.5 with `prefork`  Multi-Processing Module (MPM) and `mod_php`

## PHP Runtime
- 5.6+, 7.0, or 7.1

## Web Browser
- Edge (Windows 10)
- Internet Explorer 11
- Firefox 57 or 52 ESR
- Chrome 64+
- Safari 10+

## Mobile
- iOS 9+
- Android 4.0+

# INSTALLING OWNCLOUD

## Prerequisites
- Red Hat Enterprise Linux 6.9 or later is installed
- Apache is installed
- PHP is installed

## Procedure
1. Trust the ownCloud repository.  
    ```sudo rpm --import https://download.owncloud.org/download/repositories/production/RHEL_7/repodata/repomd.xml.key```

2. Add the ownCloud repository.  
    ```sudo wget http://download.owncloud.org/download/repositories/production/RHEL_7/ce:stable.repo -O /etc/yum.repos.d/ce:stable.repo```

3. Clean the `yum` cache.  
    ```sudo yum clean all```

4. Install the package.  
    ```sudo yum install owncloud-files```

5. Run the installation wizard to complete the installation.  
    1. Enter http://localhost/owncloud in your Web browser.
    2. Enter an administrator username and password.
    3. Click `Finish Setup`.

# CONFIGURE OWNCLOUD TO USE TCP PORT 8080
You can modify ownCloud to listen on a TCP port other than the default port 80. The TCP port is controlled by the Web server. For Apache, use the following instructions:

1. Edit `httpd.conf` to add the `LISTEN 8080` directive. The `httpd.conf` file is located in /etc/apache2/ directory.

2. Edit `ports.conf` to specify `Listen 8080`. The 'ports.conf' file is located in the /etc/apache2/ directory.

3. Restart Apache.  
    ````sudo service apache2 restart````
