# Filtrage-Internet
## Shémas du réseau
### Option 1 : Proxy passerelle

    Box <-----> Proxy <-----> Réseau local

**Avantage**

- Tout est filtrer / Impossible de passer à coté

**Inconvénient**

- Bloquant en cas de panne
- Changement de configuration du réseau à la mise en place

### Option 2 : Proxy élément du réseau

    Box <---+---> Réseau local
    	    |
    	    +-> Proxy	
	

**Avantage**

- Pas de gros changement sur le réseau
- Non bloquant en cas de panne ?

**Inconvénient**

- Simple à contourner

## Technos utilisées
### Page web de confirguation
[Nginx](https://fr.wikipedia.org/wiki/Nginx "Nginx") peut être utilisé comme serveur web pour sa légerté
[CherryPy](http://www.cherrypy.org/ "Cherrypy") peut être une alternative intéressante car il propose aussi un petit framworken Python.

### Proxy et filtrage
Le proxy doit supporter http et https.

[DansGuardian](http://dansguardian.org/ "dansguardian") est un bonne solution de filtrage et peut être utilisé avec un serveur proxy [Squid](http://www.squid-cache.org/ "squid") ou [Tinyproxy](https://tinyproxy.github.io/ "tinyproxy")

### Découverte de la page de configuration
Utilisation de la technologie Zeroconf / mDNS avec le logiciel [Avahi](http://www.avahi.org/ "avahi") pour permetre la découverte de la page web de configuration sur une machine "filtrage.localdomain" ou "filtrage".

### Découverte et paramétrage automatique du Proxy
[WPAD](https://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol "WPAD") permet un paramétrage automatique du proxy sur les clients via DHCP ou DNS. (Visiblement pas via Zeroconf)

### Système d'exploitation du proxy
On part sur une débian car c'est une distribution bien connue.