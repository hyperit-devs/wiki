---
description: Hier zeigen wir dir, wie du Java auf Ubuntu installieren kannst.
---

# ♨ Java Installation Ubuntu 22.04 / 20.04

{% hint style="info" %}
Um die Befehle auszuführen müssen sie sich mit ihren Login Daten bei [Putty](https://www.chiark.greenend.org.uk/\~sgtatham/putty/latest.html) anmelden.
{% endhint %}

**Schritt 1:**

Als erstes überprüfen wir unseren Server ob es Updates oder Upgrades in der Paketliste gibt.

```
apt update && apt upgrade -y
```

**Schritt 2.1:**

Ubuntu - Java 17

```
apt install openjdk-17-jre-headless -y
```

**Schritt 2.2:**

Ubuntu - Java 11

```
apt install openjdk-11-jre-headless -y
```

**Schritt 2.3:**

Ubuntu - Java 8

```
apt install openjdk-8-jre-headless -y
```

**Schritt 3:**

Nun überprüfen wir ob die von ihnen gewählte Java Version erfolgreich Installiert wurde.

```
java -version
```
