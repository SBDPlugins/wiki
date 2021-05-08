# Setup of the Panels

## ThemeParkPanel:

### Requirements:

* A webhosting with:
  * 1 MYSQL database
  * An SMTP mail server
  * Minimal PHP version 7.2 \(support\)
* A minecraft server with:
  * The ThemePark plugin
  * The ThemeParkConnector plugin

**You can install the panel in 2 ways. If you have your own VPS or your webhosting has SSH access, follow these steps. Otherwise, follow the steps for webhosting without SSH access.**

### **Installation with SSH Access support:**

#### 1. Connecting to SSH

This step is different for every webhosting. I'm going to follow the way for Vimexx, but you have to contact your Webhosting to find out the way to do it for you.

If you are using Windows, you need PuTTY or an equivalent program to connect to the SSH. You can download it at [https://www.putty.org/](https://www.putty.org/)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Windows:</th>
      <th style="text-align:left">Mac:</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <ol>
          <li>Open PuTTY</li>
          <li>Enter the hostname of your webhosting at &quot;Host Name&quot;.</li>
          <li>Enter the port of your webhosting at &quot;Port&quot;.</li>
          <li>Click on Open.</li>
          <li>Enter the username and password of your DirectAdmin account.</li>
          <li>Done! You are connected to your SSH.</li>
        </ol>
      </td>
      <td style="text-align:left">
        <ol>
          <li>Open the Terminal.</li>
          <li>
            <p>Enter the command:</p><pre><code class="lang-text">ssh -p &lt;Port&gt; &lt;Username&gt;@&lt;Hostname&gt;</code></pre>

          </li>
          <li>At &lt;Hostname&gt;, enter your hostname. At &lt;Username&gt;, enter the
            username of your DirectAdmin account. At &lt;Port&gt;, enter the port.</li>
          <li>Enter the password of your DirectAdmin account</li>
          <li>Done! You are connected to your SSH.</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>

#### 2. Connecting to FTP

You need to install [**Filezilla** ](https://filezilla-project.org/)**or** [**WinSCP** ](https://winscp.net/eng/download.php)to send the files to your webhosting. You need to install the **Client**. At Filezilla, click on the icon on the left \(**Site Manager**\), and click on **New Site**. Then fill in your **credentials of the FTP server** and click on **Connect**.

In your FTP, **select your domain** and put the **files of the SSH ZIP** into your FTP. 

#### 3. Setting up the database:

Go to the homepage of DirectAdmin and go to **MYSQL Management**. Click on **Create new Database** and fill in the data. Also, save this data somewhere, because you need it later.

{% hint style="danger" %}
After you've created it, you have to click on your database, and at **Access Hosts**, you have to put in a **% and click on Add Host**, so that the Minecraft server can find the database and can connect to it. **This is VERY important!**
{% endhint %}

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

Then run the following commands to install your panel and create your database:

```bash
composer install --no-dev --optimize-autoloader
php artisan key:generate --force
php artisan migrate --force
```

Now your database is ready for usage.

#### 5. Rewriting users to your panel \(public folder\):

{% hint style="info" %}
The step descriped below will only work if you are using an **Apache2** webserver. For the **Nginx** installation, you have to set the basepath to the /public folder. If you need help with this, please contact us in our Discord server.
{% endhint %}

Because of safety reasons, all the files who are needed for users aren't included in the main map, but in the /public folder. You have to redirect the users to this folder, by using the .htaccess file. It's included in the ZIP, but you **HAVE TO** change it.

Create a .htaccess file in the panel main folder, and put this into it:

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

_Source:_ [_https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a_](https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a)\_\_

### Installation without SSH Access:

#### 1. Setting up the database:

Go to the homepage of DirectAdmin and go to **MYSQL Management**. Click on **Create new Database** and fill in the data. Also, save this data somewhere, because you need it later.

{% hint style="danger" %}
After you've created it, you have to click on your database, and at **Access Hosts**, you have to put in a **% and click on Add Host**, so that the Minecraft server can find the database and can connect to it. **This is VERY important!**
{% endhint %}

Now you have to upload the SQL-file, so that the plugin can upload his attractions. Open your database with PHPMyAdmin, and go to Import in the menu, and then choose the SQL-file at "File to import:". Then click on the Start button. Now it's uploaded.

#### 2. Installing the panel to your webserver:

You need to install [**Filezilla** ](https://filezilla-project.org/)**or** [**WinSCP** ](https://winscp.net/eng/download.php)to send the files to your webhosting. You need to install the **Client**. At Filezilla, click on the icon on the left \(**Site Manager**\), and click on **New Site**. Then fill in your **credentials of the FTP server** and click on **Connect**.

In your FTP, **select your domain** and put the **files of the Non-SSH ZIP** into your FTP. 

Now copy the **.env.example** file and rename it to **.env**. 

Then you have to change the settings in the **.env** file. Change the **APP\_URL** to the url of your panel, and **STORE\_URL** to the url of your store.

At **DB\_** you can change the database credentials of the database you created.

For the **MAIL\_** settings you have to create a mail account, and then lookup the **SMTP** server from your hosting. Ask your hosting for support if you are unable to do this.

{% hint style="warning" %}
**Pay attention!** Some hostings are using SSL or no encryption for the SMTP server. Then leave the MAIL\_ENCRYPTION setting empty.
{% endhint %}

#### 3. Rewriting users to your panel \(public folder\):

Because of safety reasons, all the files who are needed for users aren't included in the main map, but in the /public folder. You have to redirect the users to this folder, by using the .htaccess file.

Create a .htaccess file in the panel main folder, and put this into it:

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

_Source:_ [_https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a_](https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a)\_\_

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

