---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2024-04-28T14:39:00
Status: Not started
Description: ""
---
- [x] 1. Criação de uma pipeline, a qual terá uma aplicação web (escolhida nos exercícios anteriores).
- [x] 2. Essa aplicação precisará estar hospedada no Docker Hub e possuir um teste de segurança, utilizando SAST ou DAST, conforme veremos na próxima semana (semana 8).
- [x] 3. Envio da notificação para o Telegram ou Discord após o Pull Request (PR).Caso utilize o GitLab, consulte esta página como referência: [https://docs.gitlab.com/ee/ci/variables/predefined_variables.html](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html), assim como a pipeline de exemplo: https://gitlab.com/michelleamesquita/devsecops2/.
- [x] 4. Criação de uma pipeline com as fases build, test e deploy (a produção pode ser feita utilizando o Ngrok, caso não utilize a nuvem, visto que para o GitLab encontrar a aplicação e testá-la, precisa que esteja hospedada na internet).
- [x] A entrega da atividade deve ser feita na semana 8, em um documento com o** link do repositório Git**, com o **print da pipeline**, mostrando que você conseguiu rodar uma aplicação web, podendo conter ou não alguma vulnerabilidade na aplicação e fazendo o deploy.