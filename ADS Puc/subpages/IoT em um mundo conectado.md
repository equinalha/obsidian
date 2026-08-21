---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2023-09-01T15:14:00
Status: Not started
Description: ""
---
# MQTT

![[ADS Puc/images/Untitled 3.png]]

![[ADS Puc/images/Untitled 4.png]]

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

![[ADS Puc/images/Untitled 5.png]]

![[ADS Puc/images/Untitled 6.png]]

![[ADS Puc/images/Untitled 7.png]]

![[ADS Puc/images/Untitled 8.png]]

![[ADS Puc/images/Untitled 9.png]]

![[ADS Puc/images/Untitled 10.png]]

![[ADS Puc/images/Untitled 11.png]]

![[ADS Puc/images/Untitled 12.png]]

![[ADS Puc/images/Untitled 13.png]]

![[ADS Puc/images/Untitled 14.png]]