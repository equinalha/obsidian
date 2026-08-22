---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:17:00
Owner:
  - Eduardo Quinalha
---
# Conceitos

- Pilares
	- **Confiável**, engajante e rápida
	- **Permite o uso offline**
	- **Pode ser utilizada como app nativa**
- Envolve frontend e backend
- Oferecem experiências similares a de **aplicativos nativos **instalados no dispositivo
- Baixo consumo de recursos
- Deve ser pelo menos **parcialmente disponível offline**

## Características

- **Relevantes:** Funcionam em qualquer navegador da web, independentemente do dispositivo utilizado (desktop, celular, tablet).
- **Instaláveis****:** Podem ser instalados na tela inicial do dispositivo, como um aplicativo nativo, permitindo acesso offline e por ícone.
- **Responsivos:** Se adaptam automaticamente a diferentes tamanhos de tela, garantindo uma ótima experiência de usuário.
- **Engajadores:** **Enviam notificações push **para manter os usuários informados e engajados com o aplicativo.
- **Carregamento rápido:** Utilizam técnicas de cache para carregar rapidamente, mesmo em redes com baixa qualidade de conexão.
- **Seguros:** Funcionam com HTTPS para garantir a segurança da comunicação entre o dispositivo e o servidor.

## Tecnologias

- São webapps. Obrigatoriamente** rodam em navegador**
- Utiliza alguns **recursos avançados do navegador** que podem não estar disponíveis em todas as versões.
	- No entanto, isso não inviabiliza o uso da aplicação, ela continuará funcionando como uma webApp normal
- Não são nativas, não podem ser instaladas em smartphones, por exemplo
	- No entanto, alguns navegadores como o Chrome permitem que vc adicione um atalho que funcionará exatamente como se fosse uma app nativa

## Manifesto Web

- Arquivo **JSON** que fornece informações sobre a aplicação web
- **Permite que ela seja instalada no dispositivo** do usuário e tenha um comportamento semelhante ao de uma aplicação nativa.
- Define a** Aparência e o Comportamento **da PWA
- Configura a experiência de instalação
- Facilita a integração com o sistema operacional

```json
{
  "name": "My PWA App",
  "short_name": "MyPWA",
  "description": "A brief description of my app",
  "icons": [
    {
      "src": "icon-128.png",
      "sizes": "128x128",
      "type": "image/png"
    }
  ],
  "theme_color": "#4CAF50",
  "background_color": "#FFFFFF",
  "start_url": "/index.html",
  "display": "standalone",
  "scope": "/"
}
```

- O manifesto deverá ser incluído no código HTML

```json
<head>
  <link rel="manifest" href="manifest.webmanifest">
</head>
```
