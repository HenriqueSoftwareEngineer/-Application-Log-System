# Sistema de Logs - Relatórios em Nuvem

## Sistema de Monitoramento e Relatório Automatizado para Software Diversos

## Descrição

É um sistema de entregas de emails mensais com relatórios de uso completo de um determinado sistema (softwares diversos, sistema operacional, app, navegador,etc) instalado em seu computador. O usuário possui em sua máquina um determinado sistema  e faz o uso deste. Este sistema ficará registrado numa espécie de verificador online de uso completo que será **hospedado em nuvem**. É um tipo de **serviço SaaS** que fará a verificação (desempenho, uso, etc) e enviará um relatório mensal para o usuário via email. Os relatórios serão armazenados em um Banco de Dados e serão acessados via servidor.

Um módulo instalado no computador do usuário que faz a verificação do uso do sistema e envia os dados para o servidor.
Ele será um sistema de monitoramento e relatório automatizado para software diversos, uma espécie de auditor de uso do usuário.



## Funcionalidades


- Cliente-Servidor: O software cliente instalado nos dispositivos dos usuários coleta dados e envia para um servidor remoto.
- Coleta de Dados: Um módulo no cliente monitora o uso do software, coleta logs e dados de uso.
- Comunicação: Os dados são transmitidos do cliente para o servidor através de uma conexão segura (por exemplo, HTTPS).
- Armazenamento: O servidor armazena os dados em um banco de dados relacional ou NoSQL.
- Processamento e Geração de Relatórios: O servidor processa os dados coletados e gera relatórios periódicos.
- Envio de Email: Um serviço de email no servidor envia os relatórios para os usuários.

## Tecnologias Envolvidas:

- Frontend: Interface web para configuração e visualização dos relatórios (HTML, CSS, JavaScript, frameworks como React ou Angular).
- Backend: Lógica do servidor para processamento de dados, geração de relatórios e envio de emails (Node.js, Python, Java, Ruby).
- Banco de Dados: Armazenamento dos dados de uso (MySQL, PostgreSQL, MongoDB).
Comunicação: APIs RESTful ou gRPC para a comunicação entre cliente e servidor.
- Serviço de Email: SMTP, serviços de terceiros como SendGrid, Amazon SES.
- Segurança: TLS/SSL para comunicação segura, autenticação e autorização (OAuth, JWT).

## Modelo de Negócio:

- Software como Serviço (SaaS): Os clientes pagam uma assinatura para usar o sistema.
- Freemium: Funçes básicas gratuitas, com recursos avançados disponíveis por uma taxa.
- Licenciamento: Licenças de software que incluem suporte e atualizaçes.
- Pay-Per-Use: Cobrança baseada na quantidade de relatórios ou volume de dados processados.


## Coleta de Informaçes de Uso

A coleta das informaçes de uso do software pelo usuário pode ser feita da seguinte forma:

### Instrumentação do Software Cliente:

- Módulo de Monitoramento: Um componente é embutido no software cliente que rastreia eventos de uso, como aberturas de sessão, tempo de atividade, funcionalidades usadas, erros, etc.
Logs de Uso: Os eventos monitorados são registrados em logs locais.
Transmissão dos Dados:

- Agendador de Envio: Periodicamente, um agendador (cron job ou serviço de fundo) no cliente envia os logs coletados para o servidor remoto.
API de Coleta: O cliente faz requisições HTTP/HTTPS para uma API de coleta no servidor, enviando os dados de uso.

### Processamento no Servidor:
- Recepção de Dados: A API no servidor recebe os dados enviados pelo cliente.
- Armazenamento em Banco de Dados: Os dados são armazenados no banco de dados para posterior processamento.
- Análise de Dados: Scripts ou programas de análise processam os dados para gerar insights e relatórios.

### Geração e Envio de Relatórios:
- Geração Automática: Relatórios são gerados automaticamente com base nos dados coletados.
- Envio por Email: Um serviço de email envia os relatórios para os emails registrados dos usuários.

### Exemplo de Fluxo
- Monitoramento: O software cliente monitora e registra eventos de uso.
- Coleta de Dados: Dados de uso são coletados e armazenados localmente.
- Envio para Servidor: Periodicamente, os dados são enviados para o servidor remoto via API.
- Armazenamento e Processamento: O servidor armazena os dados e os processa para gerar relatórios.
- Envio de Relatórios: Os relatórios gerados são enviados automaticamente para os usuários por email.






## Estrutura de Pastas - diretórios

email-report-system/
├── client/
│   ├── logs/
│   │   └── usage.log
│   ├── src/
│   │   ├── __init__.py
│   │   ├── monitor.py
│   │   └── send_logs.py
│   ├── config.py
│   └── requirements.txt
├── server/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── api.py
│   │   ├── database.py
│   │   └── report.py
│   ├── config.py
│   ├── requirements.txt
│   └── run.py
├── scripts/
│   ├── setup_database.py
│   └── send_email.py
└── README.md


### Descrição do Diretório e dos Arquivos
1. client/
   Esta pasta contém o código relacionado ao cliente que coleta e envia logs.
   - logs/: Pasta para armazenar logs localmente.
     - usage.log: Arquivo de log onde os eventos de uso são registrados.
   - src/: Código fonte do cliente.
     - __init__.py: Arquivo para tornar a pasta um módulo Python.
     - monitor.py: Código para monitorar o uso do software e registrar logs.
     - send_logs.py: Código para enviar os logs para o servidor.
   - config.py: Arquivo de configuração do cliente (ex. URLs do servidor, informações de autenticação).
   - requirements.txt: Dependências do cliente.

2. server/
   Esta pasta contém o código do servidor que recebe, armazena e processa os logs, e envia os relatórios.
   - app/: Código fonte do servidor.
     - __init__.py: Arquivo para tornar a pasta um módulo Python.
     - api.py: Código para a API que recebe os logs do cliente.
     - database.py: Código para interagir com o banco de dados.
     - report.py: Código para processar os dados e gerar relatórios.
   - config.py: Arquivo de configuração do servidor (ex. informações do banco de dados, configurações de email).
   - requirements.txt: Dependências do servidor.
   - run.py: Script para iniciar o servidor.

3. scripts/
   Scripts auxiliares para tarefas como configuração do banco de dados e envio de emails.
   - setup_database.py: Script para configurar o banco de dados (ex. criar tabelas).
   - send_email.py: Script para enviar emails (pode ser usado para testes ou automação).

4. README.md
   Arquivo de documentação do projeto, explicando como configurar e usar o sistema.
