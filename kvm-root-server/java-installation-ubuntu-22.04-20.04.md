---
description: Hier zeigen wir dir, wie du Java auf Ubuntu installieren kannst.
---

# Java Installation Ubuntu 22.04 / 20.04

{% hint style="info" %}
Hier zeigen wir dir die Installation von den verschiedenen Java Versionen auf Debian 11
{% endhint %}

**Als erstes überprüfen wir unseren Server ob es Updates oder Upgrades in der Paketliste gibt.**

```
apt update && apt upgrade -y
```

**Ubuntu - Java 17**

```
apt install openjdk-17-jre-headless -y
```

**Ubuntu - Java 11**

```
apt install openjdk-11-jre-headless -y
```

**Ubuntu - Java 8**

```
apt install openjdk-8-jre-headless -y
```

**Nun überprüfen wir ob die von ihnen gewählte Java Version erfolgreich Installiert wurde.**

```
java -version
```
