---
description: Hier zeigen wir dir, wie du Java auf Debian installieren kannst.
---

# Java Installation Debian 11

{% hint style="info" %}
Hier zeigen wir dir die Installation von den verschiedenen Java Versionen auf Debian 11
{% endhint %}

**Als erstes überprüfen wir unseren Server ob es Updates oder Upgrades in der Paketliste gibt.**

```
apt update && apt upgrade -y
```

**Für Debian 11 - Java 17**

```
apt install openjdk-17-jre-headless -y
```

**Für Debian 11 - Java 11**

```
apt install openjdk-11-jre-headless -y
```

**Für Debian 11 - Java 8**

```
apt install apt-transport-https ca-certificates wget dirmngr gnupg software-properties-common -y
wget -qO - https://adoptopenjdk.jfrog.io/adoptopenjdk/api/gpg/key/public | apt-key add -
add-apt-repository --yes https://adoptopenjdk.jfrog.io/adoptopenjdk/deb/
apt update
apt install adoptopenjdk-8-hotspot -y

```

**Nun überprüfen wir ob die von ihnen gewählte Java Version erfolgreich Installiert wurde.**

```
java -version
```
