# Setup of the Panels

## ThemeParkPanel:

### Requirements:

* A webhosting with:
  * 1 MYSQL database
  * An SMTP mail server
  * PHP version 8.0.2 or higher
* A minecraft server with:
  * The ThemePark plugin
  * The ThemeParkConnector plugin

### Installation **on a shared hosting**:

Are you using a shared webhosting? Then follow this guide.\
If you have your own webhosting on a server, then skip to [that part](setup-of-the-panels.md#installation-without-ssh-access).

#### 1. Setting up the database:

Go to the homepage of DirectAdmin and go to **MySQL Management**. Click on **Create new Database** and fill in the data. Also, save this data somewhere, because you need it later.

{% hint style="danger" %}
After you've created it, you have to click on your database, and at **Access Hosts**, you have to put in a **% and click on Add Host**, so that the Minecraft server can find the database and can connect to it. **This is VERY important!**
{% endhint %}

Now you have to upload the SQL-file (which can be found in the Non-SSH zip), so that the plugin can upload his attractions. Open your database with PHPMyAdmin, and go to Import in the menu, and then choose the SQL-file at "File to import:". Then click on the Start button. Now it's uploaded.

#### 2. Installing the panel to your webserver:

You need to install [**Filezilla** ](https://filezilla-project.org)**or** [**WinSCP** ](https://winscp.net/eng/download.php)to send the files to your webhosting. You need to install the **Client**. At Filezilla, click on the icon on the left (**Site Manager**), and click on **New Site**. Then fill in your **credentials of the FTP server** and click on **Connect**.

In your FTP, **select your domain** and put the **files of the Non-SSH ZIP** into your FTP.&#x20;

Now copy the **.env.example** file and rename it to **.env**.&#x20;

Then you have to change the settings in the **.env** file. Change the **APP\_URL** to the url of your panel, and **STORE\_URL** to the url of your store.

At **DB\_** you can change the database credentials of the database you created.

For the **MAIL\_** settings you have to create a mail account, and then lookup the **SMTP** server from your hosting. Ask your hosting for support if you are unable to do this.

{% hint style="warning" %}
**Pay attention!** Some hostings are using SSL or no encryption for the SMTP server. Then leave the MAIL\_ENCRYPTION setting empty.
{% endhint %}

#### 3. Rewriting users to your panel (public folder):

Because of safety, all the files who are not intended for users, are in the /public folder. This means you have to redirect the users to that folder.

**There is an **_**.htaccess**_** file in the ZIP for this. Most of the time, this file works out of the box.** _It's also included below, in the case it's missing._

{% code title=".htaccess" %}
```typescript
<IfModule mod_rewrite.c>
    <IfModule mod_negotiation.c>
        Options -MultiViews
    </IfModule>
    
    RewriteEngine On
    
    RewriteCond %{REQUEST_FILENAME} -d [OR]
    RewriteCond %{REQUEST_FILENAME} -f
    RewriteRule ^ ^$1 [N]

    RewriteCond %{REQUEST_URI} (\.\w+$) [NC]
    RewriteRule ^(.*)$ public/$1 

    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ server.php
</IfModule>
```
{% endcode %}

_Source:_ [_https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a_](https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a)__

### **Installation on your own server:**

_We'll assume here that you already have a web server running. Both Apache2 and Nginx are supported. **Is this not the case**? On the internet you can find a lot of information about the installation._

#### 1. Connecting to SFTP

You need to install [**Filezilla** ](https://filezilla-project.org)**or** [**WinSCP** ](https://winscp.net/eng/download.php)to send the files to your server. You need to install the **Client**. At Filezilla, click on the icon on the left (**Site Manager**), and click on **New Site**. Then fill in your **credentials of your server** and click on **Connect**.

In your SFTP, **select your domain** and put the **files of the SSH ZIP** into your server.&#x20;

#### 2. Connecting to SSH

If you are using Windows, you need PuTTY or an equivalent program to connect to the SSH. You can download it at [https://www.putty.org/](https://www.putty.org)

| Windows:                                                                                                                                                                                                                                                                                 | Mac:                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li>Open PuTTY</li><li>Enter the hostname of your webhosting at "Host Name".</li><li>Enter the port of your webhosting at "Port".</li><li>Click on Open.</li><li>Enter the username and password of your DirectAdmin account.</li><li>Done! You are connected to your SSH.</li></ol> | <ol><li>Open the Terminal.</li><li><p>Enter the command: </p><pre><code>ssh -p &#x3C;Port> &#x3C;Username>@&#x3C;Hostname></code></pre></li><li>At &#x3C;Hostname>, enter your hostname. At &#x3C;Username>, enter the username of your DirectAdmin account. At &#x3C;Port>, enter the port.</li><li>Enter the password of your DirectAdmin account</li><li>Done! You are connected to your SSH.</li></ol> |

#### 3. Setting up the database:

First, we install a MariaDB server. If you already have one running, skip these commands.

```bash
curl -sS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup | sudo bash
apt -y install mariadb-server
```

Then we setup the database itself.

```sql
mysql -u root -p

# Make sure to replace 'yourPassword' with a secure password
CREATE USER 'themeparkpanel'@'%' IDENTIFIED BY 'yourPassword';
CREATE DATABASE panel;
GRANT ALL PRIVILEGES ON panel.* TO 'themeparkpanel'@'%' WITH GRANT OPTION;
exit
```

We need to allow external access to this database, to make sure the Minecraft server can also connect to it.

Open your _my.cnf_ file, and add the following text to the bottom:

```
[mysqld]
bind-address=0.0.0.0
```

_Not sure where you can find your my.cnf file? Use `find /etc -iname my.cnf` to locate it._

Then run `systemctl restart mariadb` to restart your MariaDB server.

#### 4. Editing the config and running installation

Run the following commands:

```bash
cp .env.example .env
nano .env
```

Then change all the settings in that file. Change the **APP\_URL** to the url of your panel, and **STORE\_URL** to the url of your store.

At **DB\_** you can change the database credentials of the database you created.

For the **MAIL\_** settings you have to create a mail account, and then lookup the **SMTP** server from your hosting. Ask your hosting for support if you are unable to do this.

{% hint style="warning" %}
**Pay attention!** Some hostings are using SSL or no encryption for the SMTP server. Then leave the MAIL\_ENCRYPTION setting empty.
{% endhint %}

Then run the following commands to install your panel and populate your database:

```bash
composer install --no-dev --optimize-autoloader
php artisan key:generate --force
php artisan migrate --force
```

Now your database is ready for usage.

#### 5. Rewriting users to your panel (public folder):

Because of safety, all the files who are not intended for users, are in the /public folder. This means you have to redirect the users to that folder.

**Please choose the type of web server you are using.**

{% tabs %}
{% tab title="Apache2" %}
**There is an **_**.htaccess**_** file in the ZIP. Most of the time this file works fine.** _It's also included below, in the case it's missing._



{% code title=".htaccess" %}
```typescript
<IfModule mod_rewrite.c>
    <IfModule mod_negotiation.c>
        Options -MultiViews
    </IfModule>
    
    RewriteEngine On
    
    RewriteCond %{REQUEST_FILENAME} -d [OR]
    RewriteCond %{REQUEST_FILENAME} -f
    RewriteRule ^ ^$1 [N]

    RewriteCond %{REQUEST_URI} (\.\w+$) [NC]
    RewriteRule ^(.*)$ public/$1 

    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ server.php
</IfModule>
```
{% endcode %}

_Source:_ [_https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a_](https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a)__
{% endtab %}

{% tab title="Nginx With SSL" %}
Nginx uses config files for setup. Below is an EXAMPLE configuration, which can be used to redirect users to the /public folder, while also supporting HTTPS / SSL.

Make sure to replace %DOMAIN% (everywhere) by your full domain, and %PATH% by the full installation path.

This config assumes you are using PHP 8.0. If you have another PHP version installed, please change the version on line 28.

{% code title="/etc/nginx/sites-available/themeparkpanel.conf" %}
```nginx
server {
        listen 80;
        listen [::]:80;

        server_name %DOMAIN%;
        return 301 https://$server_name$request_uri;
}

server {
        listen 443 ssl http2;
        listen [::]:443 ssl http2;
        
        ssl_certificate /etc/letsencrypt/live/%DOMAIN%/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/%DOMAIN%/privkey.pem;

        root /%PATH%/public;

        index index.php index.html index.htm index.nginx-debian.html;

        server_name example.com www.example.com;

        location / {
                try_files $uri $uri/ /index.php?$query_string;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php8.0-fpm.sock;
        }

        location ~ /\.ht {
                deny all;
        }

        location ~ /.well-known {
                allow all;
        }
}
```
{% endcode %}

Then you need to enable your configuration, like this:

```bash
# If you use CentOS, you can ignore this command.
sudo ln -s /etc/nginx/sites-available/themeparkpanel.conf /etc/nginx/sites-enabled/themeparkpanel.conf

# Then restart NGINX
systemctl restart nginx
```
{% endtab %}

{% tab title="NGINX Without SSL" %}
Nginx uses config files for setup. Below is an EXAMPLE configuration, which can be used to redirect users to the /public folder.

Make sure to replace %DOMAIN% (everywhere) by your full domain, and %PATH% by the full installation path.

This config assumes you are using PHP 8.0. If you have another PHP version installed, please change the version on line 28.

{% code title="/etc/nginx/sites-available/themeparkpanel.conf" %}
```nginx
server {
        listen 80;
        listen [::]:80;
        
        root /%PATH%/public;
        
        server_name %DOMAIN%;
        index index.php index.html index.htm index.nginx-debian.html;

        server_name example.com www.example.com;

        location / {
                try_files $uri $uri/ /index.php?$query_string;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/run/php/php8.0-fpm.sock;
        }

        location ~ /\.ht {
                deny all;
        }

        location ~ /.well-known {
                allow all;
        }
}
```
{% endcode %}

Then you need to enable your configuration, like this:

```bash
# If you use CentOS, you can ignore this command.
sudo ln -s /etc/nginx/sites-available/themeparkpanel.conf /etc/nginx/sites-enabled/themeparkpanel.conf

# Then restart NGINX
systemctl restart nginx
```
{% endtab %}
{% endtabs %}

## ThemeParkPanelPlus:

#### 1. Installing the panel:

The installation of the Plus panel is very simple! Just extract all the files of the ThemeParkPanelPlus ZIP into the main folder of the panel.

Then go to routes/web.php and add this at the bottom of the file:

{% code title="web.php" %}
```php
//ThemeParkPanelPlus
Route::get('/control/{attraction_id}/{pin}', 'ControlController@index');
```
{% endcode %}

#### 2. Setting up the panel:

Open the **.env** file. Add this at the bottom of the file:

{% code title=".env" %}
```javascript
CONTROL_ID=CHANGEME
```
{% endcode %}

Change the **CHANGEME** to the ID that you made up in the **settings.yml** file of the **Connector** plugin.

{% hint style="info" %}
The panel URL for the ThemeParkConnector plugin changed with the newest version of the panel. Please make sure it looks like the code below.
{% endhint %}

{% code title="settings.yml" %}
```yaml
socket:
  panel: "https://domain.com/control/%ATTRACTION%/%PIN%"
```
{% endcode %}
