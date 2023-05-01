---
description: Hier zeigen wir dir, wie du Java auf Debian installieren kannst.
---

# ♨ Java Installation Debian 11

{% hint style="info" %}
Um die Befehle auszuführen müssen sie sich mit ihren Login Daten bei [Putty](https://www.chiark.greenend.org.uk/\~sgtatham/putty/latest.html) anmelden.
{% endhint %}

**Schritt 1:**

Als erstes überprüfen wir unseren Server ob es Updates oder Upgrades in der Paketliste gibt.

```
apt update && apt upgrade -y
```

**Schritt 2.1:**

Für Debian 11 - Java 17

```
apt install openjdk-17-jre-headless -y
```

**Schritt 2.2:**

Für Debian 11 - Java 11

```
apt install openjdk-11-jre-headless -y
```

**Schritt 2.3:**

Für Debian 11 - Java 8

```
apt install apt-transport-https ca-certificates wget dirmngr gnupg software-properties-common -y
wget -qO - https://adoptopenjdk.jfrog.io/adoptopenjdk/api/gpg/key/public | apt-key add -
add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
apt update
apt install adoptopenjdk-8-hotspot -y

```

**Schritt 3:**

Nun überprüfen wir ob die von ihnen gewählte Java Version erfolgreich Installiert wurde.

```
java -version
```
