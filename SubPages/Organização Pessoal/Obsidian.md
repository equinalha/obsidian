---

---
Mudando para o Obsidian:

- Full page width:
	- Configurações → Editor → Exibição → Margens de tamanho confortável
	- Configurações → Aparência → Fragmentos CSS
- Ícones:
	- Plugin Iconize
		- Toggle icon in tabs
		- Toggle icon in title
- URL Cards
	- Auto Card Link Plugin
- Colunas
	- Obsidian Columns (Columns) 
[https://github.com/tnichols217/obsidian-columns](https://github.com/tnichols217/obsidian-columns)
- Sincronismo:
	- No PC → plugin git
	- no celular → Usar o app **Git Sync**
[https://play.google.com/store/apps/details?id=com.viscouspot.gitsync&pli=1](https://play.google.com/store/apps/details?id=com.viscouspot.gitsync&pli=1)
- Criptografia
	- Meld Encrypt (funcionou perfeitamente)
```yaml
To use the col callout, create a callout with the col name:
> [!col]
> A col callout
>
> Second column of the callout
    
  
To use the col-md callout, create a col-md callout within the col callout
> [!col]
> A col callout
>
>> [!col-md]
>> The second column of the callout
>> 
>> More lines on the second column of the callout
    The col-md callout's width can be adjusted by adding the width after the col-md name:
> [!col]
> A col callout
>
>> [!col-md-3]
>> The second column of the callout
>> 
>> This column is now 3 times the width of the first column
    
```