---

---
[SNAP no Linux Mint](https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html)
[https://www.youtube.com/watch?v=h8LxU-JZt_s](https://www.youtube.com/watch?v=h8LxU-JZt_s)
[https://www.reddit.com/r/Fusion360/comments/162to7t/whats_the_current_state_of_fusion_360_on_linux/?tl=pt-br&rdt=55462](https://www.reddit.com/r/Fusion360/comments/162to7t/whats_the_current_state_of_fusion_360_on_linux/?tl=pt-br&rdt=55462)
[https://github.com/cryinkfly/Autodesk-Fusion-360-for-Linux/issues/421](https://github.com/cryinkfly/Autodesk-Fusion-360-for-Linux/issues/421)
# Post Installation

- Update
- Boost tweaks
	- Preload:
		- Monitora o uso de aplicativos, deixando aqueles mais frequentes pré-carregados na memória, acelerando a inicialização dos mesmos
	- Atalhos de teclado:
		- Super + <num> → Inicia a aplicação pinada na barra de tarefas onde <num> corresponde a posição
	- Usar DNS do google
	- TLP - Boost da bateria do laptop
		- `sudo apt install tlp tlp-rdw`
	- Usar GPU para acelerar o Firefox
		- Acessar: `about:config`
		- Colar: `layers.acceleration.force-enabled`
		- Alterar para `True`
		- Colar: `gfx.webrender.all`
		- Alterar para `True`
	- Bleachbit
		- Limpeza e housekeeping
- Security Tweaks
	- Timeshift
	- Firewall
- Spices
	- Extensions