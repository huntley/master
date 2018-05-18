[Preface](#PREFACE#)  
[Requirements](#OWNCLOUD-REQUIREMENNTS)  
[Installing ownCloud](#INSTALLING-OWNCLOUD)  
[Configuring ownCloud](#CONFIGURING-OWNCLOUD-TO-USE-TCP-PORT-8080)  
[Adding a User to ownCloud](#ADDING-A-USER-TO-OWNCLOUD)  
[Connectinog to ownCloud](#CONNECTING-TO-OWNCLOUD)



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

# CONFIGURING OWNCLOUD TO USE TCP PORT 8080
You can modify ownCloud to listen on a TCP port other than the default port 80. The TCP port is controlled by the Web server. For Apache, use the following instructions:

1. Edit `httpd.conf` to add the `LISTEN 8080` directive. The `httpd.conf` file is located in /etc/apache2/ directory.

2. Edit `ports.conf` to specify `Listen 8080`. The 'ports.conf' file is located in the /etc/apache2/ directory.

3. Restart Apache.  
    ````sudo service apache2 restart````

4. Modify your firewall rules to allow incoming connections on TCP port 8080.

# ADDING A USER TO OWNCLOUD
Add users to provide access to ownCloud.
1. Open the User management page of the ownCloud Web UI.  

2. Enter a username and password for the new user in the fields above the user list.  

3. Optionally, assign the user to a group.  

4. Click `Create`.  

If you checked `Send email to new user` in the control panel on the lower left sidebar, you can enter the email address of the user and ownCloud will send the user a message with their account information.

# CONNECTING TO OWNCLOUD
Users can access ownCloud using their desktop browser or mobile device.

1. Install an ownCloud client.  

    Desktop clients are available for Windows, MacOS X, and Linux. Mobile clients are available for iOS and Android mobile devices.

2. Open the client and enter the IP address and port of the ownCloud server.  

    For example, for an ownCloud server with an IP address of 192.168.10.10, the server address is `http://192.168.10.10:8080/owncloud`
