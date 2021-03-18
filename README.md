<h1></h1>
<p align="center">
    <img src="src/Controllers/Classes/Temp/myzap.png" width="250">
    <h1 align="center">MyZAP-Flow</h1>
    <p align="center">MyZAP-Flow é um projeto open source que conecta o Dialogflow ao WhatsApp<br>dando suporte nativo para o reconhecimento de áudios e permite a conexão<br>com outras plataformas por meio de sua API REST.</p>

</p>
<p align="center">
    <img src="https://img.shields.io/github/package-json/v/NiedsonEmanoel/myzap-flow">
    <img src="https://github.com/NiedsonEmanoel/Myzap-Flow/actions/workflows/node.js.yml/badge.svg?branch=main">
    <img src="https://img.shields.io/github/languages/code-size/NiedsonEmanoel/myzap-flow">
</p>
<p align = "center">
    <img src="https://shields.io/badge/license-MIT-green">
</p>
<h1></h1>

<h1>Instalação:</h1>

<p><strong>Para esse projeto é recomendado que se utilize o Node v14, pois se trata de uma versão nova e estável, garantindo a execução do código sem maiores problemas.</strong></p>

<p>Antes que seja efetuado o clone desse projeto você tem que ter em mãos os seguintes arquivos e/ou links:</p>
<ul>
    <li><strong>Link do seu banco de dados Mongo DB</strong></li>
    <span>Ele é similar a esse: <strong>mongodb://localhost:27017/myzap-db</strong>  (Onde o myzap-db é o nome do banco, você pode colocar o que quiser.)</br></span>
    <span><br/>Você pode conseguir um banco de dados mongo com até 512Mb de armazenamento gratuito em:</br>https://www.mongodb.com/cloud/atlas/signup (Solução oficial do Mongo)</br></br>Caso você queira rodar localmente indico esse tutorial do Youtube:</br>https://www.youtube.com/watch?v=aYRkF7sHrbk</span>
    <h1></h1>
    <li><strong>Arquivo JSON do seu projeto Google Cloud Platforms</strong></li>
    <span>Esse arquivo é fundamental para que seja efetuada a comunicação com seu Chatbot do Dialogflow </br>Caso você não a tenha siga os passos da sessão <a href="https://github.com/NiedsonEmanoel/Myzap-Flow#configurando-o-dialogflow">Configurando o Dialogflow</a>.</span>
    <h1></h1>
    <li><strong>Nome do seu projeto Google Cloud Plataforms</strong></li>
    <p>É o identificador único do seu projeto, geralmente está contido dentro do JSON, mas caso você não saiba na aba <a href="https://github.com/NiedsonEmanoel/Myzap-Flow#configurando-o-dialogflow">Configurando o Dialogflow</a> é mostrado como fazer a coleta deste dado.</p>
    <h1></h1>
    <p> <i><b>Nota do desenvolvedor:</b></br>No arquivo .json contém o nome do seu projeto então por causa disto nas  versões futuras pretendo fazer essa coleta de forma automatizada.</i> </p>
</ul>

#

<h1>Instalação do Projeto</h1>

Para clonar o projeto em seu computador local execute o seguinte comando:
```sh
git clone https://github.com/NiedsonEmanoel/Myzap-Flow
```
#

### Logo após o clone do projeto é necessário que você copie o arquivo .env-example para um arquivo .env

#
Windows:
```sh
cd src/
```
```sh
cp .env-example .env
```

#
Linux ou Mac:
```sh
cd src/ && cp .env-example .env
```
# 

<h2>Com o arquivo .env criado, vamos configura-lo</h2>
<p>O arquivo .env configura as variáveis de ambiente de nossa aplicação, configurar ele é um passo obrigatório.</p>
<p>A notação " <b>./</b>  " se refere a pasta src/ do projeto, então coloque seus arquivos dentro dessa pasta.</p> 

```sh
#Coloque abaixo o link do seu banco de dados mongo, não se preocupe com a configuração, o myzap configura automaticamente.
MONGO=mongodb://localhost:27017/yourdatabase

#Localização do seu arquivo json dflow
JSON_LOCATION =./seuarquivo.json

#Nome do seu projeto Google
GCP_PROJECT_NAME=name

#Idioma do BOT
LANGUAGE_CODE=pt-BR

#Porta da aplicação
PORT=3000

#HTTPS está habilitado? 0-> Não, 1-> Sim
useHTTPS=0

#Localização do Certificado
CERT_CRT=./

#Localização da Chave privada
CERT_KEY=./

#TOKENDialogflow=eb68ebf61f2dc69f3eb084531bb5dc52

#Segredo do JWT:
SECRET=86d0f103bf15d37ebb1f5a23a1a4dd06

#Intent que redireciona o usuário para o modo de atendimento ao cliente
INTENT_SAC=Atendimento

#Limites de caracteres por mensagem. 256 é o limite do dialogflow.
CHAR_LIMIT_PER_MESSAGE=256

#Enviar mensagem de verificação para o próprio número? 0-> Não, 1-> Sim
SEND_NO_PISHING=0

#Limite de sessões simultâneas
SESSION_LIMIT=16
```

#

<h1>Conhecendo o DialogFlow</h1>
<p>O DialogFlow (antigo api.ai) é uma plataforma de criação de chatbots da Google com foco no processamento de linguagem natural. O processamento de linguagem natural é utilizado por diversos recursos de inteligência artificial, o seu objetivo é entender a frase e formar a melhor resposta possível para aquela frase. Ele está dividido em diversas fases. Normalização, Remoção de numerais, Remoção de Stopwords, Correção ortográfica, Stemização e Lematização. Essas etapas fazem, basicamente, a quebra da frase, para que seja possível compreender os significados e assim saber em que contexto devemos encaixar o sentido da frase.</p>

#

<h1>Configurando o DialogFlow</h1>

 Vá até as configurações do DialogFlow, guarde o nome do projeto e clique no nome dele para acessarmos o painel do GCP.

 ![](https://github.com/NiedsonEmanoel/Myzap-Flow/raw/092b418ec28ff35be186d48882812911db965e6a/assets/3.png)
#

 Entre no GCP e vá até APIs e serviços e logo após vá em credenciais.
  
![](https://github.com/NiedsonEmanoel/Myzap-Flow/raw/092b418ec28ff35be186d48882812911db965e6a/assets/4.png)
#

Vá em contas de serviço e clique no primeiro e-mail que aparecer.

![](https://github.com/NiedsonEmanoel/Myzap-Flow/raw/092b418ec28ff35be186d48882812911db965e6a/assets/5.png)
#

Clique em criar chave, nova chave, escolha o formato JSON e faça o download para seu computador.

![](https://github.com/NiedsonEmanoel/Myzap-Flow/raw/092b418ec28ff35be186d48882812911db965e6a/assets/6.png)


Guarde essa chave dentro da pasta `src/` e jamais suba ela no github pois ela é a autenticadora do seu projeto e em mãos erradas pode lhe trazer grandes dores de cabeça.
#

<h2>Agradecimentos:</h2>

#

## Sobre o autor [META]
Niedson Emanoel – Instagram: [@niedsonemanoel](https://instagram.com/niedsonemanoel) – [contato@niedsonemanoel.com.br](mailto:contato@niedsonemanoel.com.br)

Distribuído sob a licença MIT. Veja `LICENSE` para mais informações.
#

## Contribua

1. Faça o _fork_ do projeto (<https://github.com/NiedsonEmanoel/Myzap-Flow/fork>)
2. Crie uma _branch_ para sua modificação (`git checkout -b feature/fooBar`)
3. Faça o _commit_ (`git commit -am 'Add some fooBar'`)
4. _Push_ (`git push origin feature/fooBar`)
5. Crie um novo _Pull Request_