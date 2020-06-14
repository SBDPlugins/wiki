---
description: 'De installatie van ThemePark is eenvoudig, als je deze handleiding volgt!'
---

# De installatie

## Installatie van de plugins:

### [Gratis versie:](https://www.spigotmc.org/resources/themepark.48648/)

Download de plugin van Spigot, en installeer deze in de map **/plugins**. De plugin doet alles voor je, en je kunt alles in de bestanden wijzigen. Als je alle functies van ThemeParkPlus Basic wilt gebruiken, moet je nog een aantal dingen doen.

{% hint style="info" %}
Met de oude plugin was het mogelijk om via commando's attracties toe te voegen. Vanaf nu moet dit via het bestand attraction.yml gebeuren.
{% endhint %}

### Betaalde versies:

Voor de Plus plugin heb je de [Gratis ](https://www.spigotmc.org/resources/themepark.48648/)versie nodig, en [Vault ](https://dev.bukkit.org/projects/vault/files)voor het Fastpass systeem. Stop alle plugins in de map **/plugins** en **herstart** de server.

Als je het **ThemeParkPanel** gaat installeren, heb je ook de **ThemeParkConnector** plugin nodig. Deze plugin verbindt het paneel met de Spigot server, zodat het paneel kan werken. Zet deze plugin ook in de map **/plugins**. Voor gebruik met het paneel moet je de Gratis versie en de Connector aansluiten op de database die je gaat gebruiken voor het paneel. Zie stap 2 van de ThemeParkPanel installatie.

Als je de **ThemeParkPanelPlus** gaat installeren, moet je in de **settings.yml** van de **ThemeParkConnector** enkele dingen aanpassen. Verander het naar iets zoals dit:

{% code title="settings.yml" %}
```yaml
socket:
  enabled: true
  url: "wss://websocket.iobyte.nl/"
  panel: "https://panel.domain/panel/control/%ATTRATCION%/%PIN%"
  id: "CHANGEME"
```
{% endcode %}

Je hoeft de **url** niet aan te raken. Bij **panel** moet je het veranderen in de paneel URL. Als je paneel zich bevindt op **https://something.com/panel**, dan moet je daar **https://something.com/panel/control/%ATTRATCION%/%PIN%** invoeren. Ook moet je een ID verzinnen, die uniek is voor je server, zoals je servernaam. Zet hem bij de **id**.

## Installatie van ThemeParkPanel:

### Vereisten:

* Een webhosting met:
  * 1 MYSQL database
  * Een SMTP mail server
  * Minimaal PHP versie 7.2 \(support\)
* Een Minecraft server met:
  * De ThemePark plugin
  * De ThemeParkConnector plugin

**Je kunt het paneel op 2 manieren installeren. Als je webhosting toegang heeft tot SSH, volg dan deze stappen. Anders volg je de stappen voor webhosting zonder SSH-toegang.**

### **Installatie met SSH support:**

#### 1. Verbinden met SSH

Deze stap is voor elke webhosting anders. Ik ga de manier volgen voor Vimexx, maar je moet contact opnemen met je Webhosting om de manier te vinden waarop je het voor je eigen hosting moet doen.

Als je Windows gebruikt, heb je PuTTY of een gelijkwaardig programma nodig om verbinding te maken met de SSH. Je kunt dit programma downloaden op [https://www.putty.org/](https://www.putty.org/)

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
          <li>Vul de hostname van je webhosting in bij &quot;Host Name&quot;.</li>
          <li>Vul de poort van je webhosting in bij &quot;Port&quot;.</li>
          <li>Klik op Open.</li>
          <li>Vul de gebruikersnaam en het wachtwoord van je DirectAdmin account in.</li>
          <li>Klaar! Je bent nu verbonden met de SSH.</li>
        </ol>
      </td>
      <td style="text-align:left">
        <ol>
          <li>Open de Terminal.</li>
          <li>
            <p>Vul dit command in:</p><pre><code class="lang-text">ssh -p &lt;Port&gt; &lt;Username&gt;@&lt;Hostname&gt;</code></pre>

          </li>
          <li>Bij &lt;Hostname&gt;, vul je de hostname in. Bij &lt;Username&gt;, de
            gebruikersnaam van je DirectAdmin account. En bij &lt;Port&gt;, de poort
            van je webhosting.</li>
          <li>Vul het wachtwoord van je DirectAdmin account in.</li>
          <li>Klaar! Je bent nu verbonden met de SSH.</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>

#### 2. Verbinden met de FTP

Je moet [**Filezilla** ](https://filezilla-project.org/)**of** [**WinSCP** ](https://winscp.net/eng/download.php)hebben om bestanden te uploaden naar je webhosting. Ik volg nu even de stappen voor Filezilla. Klik op het icoon links \(**Site Manager**\), en klik op **New Site**. Vul dan de **gegevens van de FTP server in** en klik op **Connect**.

In je FTP, **selecteer je domein** en doe de **bestanden van de SSH ZIP** in je FTP. 

#### 3. De database instellen:

Ga naar de homepagina van je DirectAdmin en klik op **MYSQL Management**. Klik op **Create new Database** en vul de benodigde data in. Bewaar deze gegevens ook ergens, want je hebt ze later nodig.

{% hint style="danger" %}
Nadat je het hebt aangemaakt, moet je **op je database klikken**, en bij **Access Hosts** moet je een **%** invoeren en op **Add Host** klikken, zodat de Minecraft-server de database kan vinden en er verbinding mee kan maken. **Dit is HEEL belangrijk!**
{% endhint %}

#### 4. De config aanpassen en de installatie uitvoeren:

Voer de volgende commando's uit:

```bash
cp .env.example .env
nano .env
```

Wijzig dan alle instellingen in dat bestand. Verander de **APP\_URL** in de url van je paneel, en **STORE\_URL** in de url van je webshop.

Bij **DB\_** kun je de databasegegevens van de door jou aangemaakte database wijzigen.

Voor de **MAIL\_** instellingen moet je een mailaccount aanmaken en vervolgens de **SMTP-server** van je hosting opzoeken. **Vraag je hosting om hulp** als je niet in staat bent om dit te doen.

{% hint style="warning" %}
**Let op!** Sommige hostings gebruiken SSL of geen encryptie voor de SMTP-server. Laat dan de MAIL\_ENCRYPTION instelling leeg.
{% endhint %}

Voer dan de volgende commando's uit om je paneel te installeren en de database gegevens aan te maken:

```bash
composer install --no-dev --optimize-autoloader
php artisan key:generate --force
php artisan migrate --force
```

Nu is je database klaar voor gebruik.

#### 5. Gebruikers doorsturen naar je paneel \(public map\):

Omwille van veiligheidsredenen zijn alle bestanden die nodig zijn voor bezoekers niet opgenomen in de hoofdmap, maar in de /public map. Je moet de bezoekers omleiden naar deze map, door gebruik te maken van het **.htaccess** bestand.

Maak een .htaccess bestand aan in de hoofdmap van het paneel en zet dit erin:

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

_Code van:_ [_https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a_](https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a)\_\_

### Installation without SSH Access:

#### 1. De database instellen:

Ga naar de homepagina van je DirectAdmin en klik op **MYSQL Management**. Klik op **Create new Database** en vul de benodigde data in. Bewaar deze gegevens ook ergens, want je hebt ze later nodig.

{% hint style="danger" %}
Nadat je het hebt aangemaakt, moet je **op je database klikken**, en bij **Access Hosts** moet je een **%** invoeren en op **Add Host** klikken, zodat de Minecraft-server de database kan vinden en er verbinding mee kan maken. **Dit is HEEL belangrijk!**
{% endhint %}

Nu moet je het SQL-bestand uploaden, zodat de plugin zijn attracties kan uploaden. Open je database met PHPMyAdmin, en ga naar Importeren in het menu, en kies dan het SQL-bestand bij "Bestand om te importeren:". Klik vervolgens op de knop Start. Nu is hij geüpload.

#### 2. Installing the panel to your webserver:

Je moet [**Filezilla** ](https://filezilla-project.org/)**of** [**WinSCP** ](https://winscp.net/eng/download.php)hebben om bestanden te uploaden naar je webhosting. Ik volg nu even de stappen voor Filezilla. Klik op het icoon links \(**Site Manager**\), en klik op **New Site**. Vul dan de **gegevens van de FTP server in** en klik op **Connect**.

In je FTP, **selecteer je domein** en doe de **bestanden van de Non-SSH ZIP** in je FTP. 

Kopieer nu het **.env.example** bestand en hernoem het naar **.env**.

Wijzig dan alle instellingen in dat bestand. Verander de **APP\_URL** in de url van je paneel, en **STORE\_URL** in de url van je webshop.

Bij **DB\_** kun je de databasegegevens van de door jou aangemaakte database wijzigen.

Voor de **MAIL\_** instellingen moet je een mailaccount aanmaken en vervolgens de **SMTP-server** van je hosting opzoeken. **Vraag je hosting om hulp** als je niet in staat bent om dit te doen.

{% hint style="warning" %}
**Let op!** Sommige hostings gebruiken SSL of geen encryptie voor de SMTP-server. Laat dan de MAIL\_ENCRYPTION instelling leeg.
{% endhint %}

#### 3. Gebruikers doorsturen naar je paneel \(public map\):

Omwille van veiligheidsredenen zijn alle bestanden die nodig zijn voor bezoekers niet opgenomen in de hoofdmap, maar in de /public map. Je moet de bezoekers omleiden naar deze map, door gebruik te maken van het **.htaccess** bestand.

Maak een .htaccess bestand aan in de hoofdmap van het paneel en zet dit erin:

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

_Code van:_ [_https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a_](https://gist.github.com/liaotzukai/8e61a3f6dd82c267e05270b505eb6d5a)\_\_

## Installatie van ThemeParkPanelPlus:

#### 1. Het paneel installeren:

De installatie van het Plus-paneel is zeer eenvoudig! Je hoeft alleen maar alle bestanden van het ThemeParkPanelPlus ZIP uit te pakken in de hoofdmap van het paneel.

Ga dan naar routes/web.php en voeg dit toe onderaan het bestand:

{% code title="web.php" %}
```php
//ThemeParkPanelPlus
Route::get('/control/{attraction_id}/{pin}', 'ControlController@index');
```
{% endcode %}

#### 2. Het paneel instellen:

Open het .env-bestand. Voeg dit toe aan het einde van het bestand:

{% code title=".env" %}
```javascript
CONTROL_ID=CHANGEME
```
{% endcode %}

Verander de **CHANGEME** naar de ID die je hebt verzonnen in het **settings.yml** bestand van de **Connector** plugin.

## Installatie van ActionFoto:

Download de plugin op de site, en installeer deze in je /plugins map. De plugin doet alles voor je, en je kunt alles in de bestanden wijzigen.

**Er zijn 2 vereiste plugins die nodig zijn. Die kun je** [**hier**](https://www.spigotmc.org/resources/api-mapmanager.19198/) **en** [**hier**](https://www.spigotmc.org/resources/api-packetlistenerapi.2930/) **vinden.**

## Installatie van de **ThemeParkPlus ridecount add-on**:

Je moet deze plugin net als ActionFoto installeren. Download de plugin op de site, installeer hem in je /plugins map.

**Let op: deze plugin gebruikt dezelfde vereisten als ActionFoto.**

