---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2023-09-01T15:14:00
Status: Not started
Description: ""
---
# MQTT

![[SubPages/ADS - PUC-PR/images/Untitled 3.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 4.png]]

# Wildcards

- +
	- Usado pelos subscribers
	- myhome/groundfloor/+/temperature
		- Pode equivaler com qualquer coisa como:
			- myhome/groundfloor/**kitchen**/temperature
			- myhome/groundfloor/**livingroom**/temperature
- #
	- Somente por subscribers
	- Vários níveis
	- Sempre no final do tópico
	- myhome/groundfloor/#

# Last Will and Testament (LWT)

- Configurado no ato da conexão
- Instrui sobre o que fazer se o dispositivo ficar inativo

![[SubPages/ADS - PUC-PR/images/Untitled 5.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 6.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 7.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 8.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 9.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 10.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 11.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 12.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 13.png]]

![[SubPages/ADS - PUC-PR/images/Untitled 14.png]]