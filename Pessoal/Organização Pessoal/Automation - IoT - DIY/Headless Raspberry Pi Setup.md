---

---
```shell
Finally we need to enable ssh and connect to wifi. Open File Explorer and click on 'boot' on the left side. You should be presented with a list of files. Right click and create a new text document, then name it ssh and remove the .txt extension at the end. Note, you will have to have 'Show File Extensions' enabled in order to do this. Click Yes and an empty file called ssh should be present. Next we need to create a text document again, but name it wpa_supplicant , replacing the .txt with .conf. Right Click it and select edit and paste this text into the file, substituting your wifi details in:

country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
ssid="WIFI_SSID"
scan_ssid=1
psk="WIFI_PASSWORD"
key_mgmt=WPA-PSK
}
```