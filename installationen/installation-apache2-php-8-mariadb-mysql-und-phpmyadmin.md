---
description: >-
  Hier zeigen wir dir, wie du Apache2, PHP8, MariaDB (MySQL) und phpmyadmin auf
  Debian & Ubuntu installierst
---

# 💻 Installation Apache2, PHP 8, MariaDB (MySQL) und phpmyadmin

{% hint style="info" %}
Um die Befehle auszuführen müssen sie sich mit ihren Login Daten bei [Putty](https://www.chiark.greenend.org.uk/\~sgtatham/putty/latest.html) anmelden.
{% endhint %}

**Schritt 1:**

Als erstes überprüfen wir unseren Server ob es Updates oder Upgrades in der Paketliste gibt.

```
apt update && apt upgrade -y
```

**Schritt 2:**

Nun installieren wir die nötigen Pakete die wir für die Installation brauchen.

```
apt install ca-certificates apt-transport-https lsb-release gnupg curl nano unzip -y
```

**Schritt 3:**

Nun fügen wir die nötigen Paketquellen hinzu.

#### Für Debian

1. Als erstes müssen wir den nötigen Key für die Paketquelle hinzufügen.&#x20;

```
curl -fsSL https://packages.sury.org/php/apt.gpg -o /usr/share/keyrings/php-archive-keyring.gpg
```

2. Um die nötige Paketquelle hinzuzufügen verwenden sie

```
echo "deb [signed-by=/usr/share/keyrings/php-archive-keyring.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
```

#### Für Ubuntu

1. Erstmal müssen wir das Paket installieren was zur Verwaltung der Paketquelle dient.

```
apt install software-properties-common -y
```

2. Nun fügen wir die Paketquelle hinzu&#x20;

```
add-apt-repository ppa:ondrej/php
```

**Schritt 4:**

Nun aktualisieren wir unseres Paketlisten

```
apt update && apt upgrade -y
```

**Schritt 5:**

Nun installieren wir unseren Webserver Apache2

```
apt install apache2 -y
```

**Schritt 6:**

Jetzt müssen wir PHP8 und einige nötigen Module Installieren.

```
apt install php8.2 php8.2-cli php8.2-common php8.2-curl php8.2-gd php8.2-intl php8.2-mbstring php8.2-mysql php8.2-opcache php8.2-readline php8.2-xml php8.2-xsl php8.2-zip php8.2-bz2 libapache2-mod-php8.2 -y
```

**Schritt 7:**

Als nächstes werden wir unseren MariaDB-Server und -Client (MySQL) installieren.

```
apt install mariadb-server mariadb-client -y
```

**Schritt 8:**

Nun müssen wir die Konfiguration für den MariaDB-Server tätigen.

```
mysql_secure_installation
```

**Schritt 9:**

Nun wechseln wir in das Verzeichnis wo phpmyadmin Installiert wird.

```
cd /usr/share
```

**Schritt 10:**

Nun laden wir uns phpmyadmin Runter

```
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.zip -O phpmyadmin.zip
```

**Schritt 11:**

Jetzt entpacken wir die Runtergeladene Datei

```
unzip phpmyadmin.zip
```

**Schritt 12:**

Jetzt kannst du das Archiv löschen was wir eben entpackt haben.

```
rm phpmyadmin.zip
```

**Schritt 13:**

Nun müssen wir das entpackte Verzeichnis zu **phpmyadmin** umbenennen.

```
mv phpMyAdmin-*-all-languages phpmyadmin
```

**Schritt 14:**

Jetzt geben wir dem Verzeichnis noch die nötigen Rechte.&#x20;

```
chmod -R 0755 phpmyadmin
```

**Schritt 15:**

Nun müssen wir ein Apache2-Konfigurationsdatei erstellen.&#x20;

```
nano /etc/apache2/conf-available/phpmyadmin.conf
```

**Schritt 16:**

Dort fügen wir folgendes ein.

```
# phpMyAdmin Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
    Options SymLinksIfOwnerMatch
    DirectoryIndex index.php
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/templates>
    Require all denied
</Directory>
<Directory /usr/share/phpmyadmin/libraries>
    Require all denied
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Require all denied
</Directory>
```

Die Konfigurationsdatei speichern wir einmal mit **STRG + X, danach Y und anschließend Enter**

**Schritt 17:**

Nun aktivieren wir unsere eben erstelle Konfigurationsdatei in Apache2 und laden Apache2 einmal neu.

```
a2enconf phpmyadmin
```

```
systemctl reload apache2
```

**Schritt 18:**

Nun erstellen wir ein Temporäres Verzeichnis was phpmyadmin benötigt.

```
mkdir /usr/share/phpmyadmin/tmp/
```

**Schritt 19:**

Nun geben wir dem Webserver-Benutzer die benötigten rechte für das Temporäre Verzeichnis

```
chown -R www-data:www-data /usr/share/phpmyadmin/tmp/
```

**Schritt 20:**

Wenn sie alles schritte befolgt haben sollten sie nun mit ihrer **IP und /phpmyadmin** nun auf die Weboberfläche kommen. Unten ist einmal ein Beispiel, ersetzen sie **127.0.0.1** durch ihre Server IP.

```
127.0.0.1/phpmyadmin
```
