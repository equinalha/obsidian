---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-12T07:42:00
Owner:
  - Eduardo Quinalha
---
# NFS

- Funciona sobre TPC/IP
- Cliente/Servidor
- Construído sobre RPC
- Na versão 4 o TCP é obrigatório
- Sistemas UNIX like
- Configurações em /etc/exports
- Exemplo

```shell
/home/trabalhos cliente (rw)
/home/músicas andre.castro(rw)
/home/vídeos 192.168.1.0/255.255.255.0(ro)
```

# CIFS

- **Windows**
- Cliente/Servidor
- Implementação do SMB
	- Também conhecido por SMB/CIFS
- Porta 445
- Utiliza NetBIOS sobre TCP (NBT)
