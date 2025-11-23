## Conceitos apresentados:

🔐 Autenticação sem estado (stateless)

O servidor não guarda sessão do usuário. As informações de autenticação (como tokens JWT) são auto-contidas e validadas a cada requisição. Vantagem: escalabilidade e menor carga de sessão. Desvantagem: revogar tokens é mais difícil.

🔒 Autenticação com estado (stateful)

O servidor mantém o estado da sessão do usuário (ex.: ID de sessão salvo em memória ou banco). Cada requisição é validada consultando esse estado. Vantagem: fácil invalidar sessões. Desvantagem: menos escalável — exige controle centralizado de sessões.

🌐 Autenticação federada

O processo de autenticação é delegado a um provedor externo (ex.: Google, Microsoft, Facebook). O usuário faz login em um serviço confiável e usa esse mesmo login em outros sistemas. Padrões comuns: OAuth 2.0, OpenID Connect, SAML. Exemplo: “Entrar com Google”.

🧩 Ataque de permutação (Permutation attack)

O atacante permuta (troca a ordem ou combinações) de partes conhecidas das credenciais (nomes, números, palavras comuns) para gerar variações de senhas. Exemplo: de “Joao2024!” gerar “2024Joao!”, “Joao!2024”, etc. É uma forma de ataque de dicionário inteligente.

⚔️ Ataque híbrido

Combina ataque de dicionário + ataque de força bruta. O atacante começa com uma lista de palavras conhecidas (dicionário) e aplica mutações automáticas (ex.: adiciona números, símbolos, letras maiúsculas/minúsculas). Exemplo: de “senha” → “Senha1”, “S3nha!”, “senha2024”, etc. Muito usado por ferramentas como Hashcat.

Password Spraying 🔒 O atacante tenta poucas senhas comuns (ex.: 123456, Password123) em muitos usuários diferentes para evitar bloqueios. Foco: descobrir contas com senhas fracas.

Credential Stuffing 🔒 O atacante usa pares de login e senha vazados de outros sites e testa em vários serviços, aproveitando quem reutiliza senhas. Foco: explorar credenciais reais obtidas em vazamentos.

## Ferramentas utilizadas 

Medusa

Objetivo principal: ferramenta de brute-force paralela para testar autenticações remotas em massa (vários hosts/contas), focada em velocidade e escala.

Uso típico: auditoria/pen-test (com autorização) para identificar credenciais fracas em serviços como SSH, FTP, etc.

Hydra (THC-Hydra)

Objetivo principal: realizar ataques de força bruta e dicionário contra serviços de autenticação remota, com amplo suporte a protocolos e opções de configuração.

Uso típico: avaliação de segurança para descobrir contas com senhas fracas ou políticas inadequadas; muito usado por pentesters.

Diferença rápida: Medusa privilegia desempenho e execução em larga escala; Hydra tem suporte mais amplo de protocolos e maior adoção/comunidade.

é: ferramenta de cracking de autenticação em rede desenvolvida pelo time do Nmap.

Objetivo principal: testar logins/serviços em rede (SSH, RDP, FTP, etc.) de forma paralela e eficiente para avaliar pontos fracos em autenticação remota.

John the Ripper (John)

O que é: um cracker de senhas para hashes (arquivo local) com múltiplos modos (dicionário, regra, força bruta, híbrido).

Objetivo principal: recuperar senhas a partir de hashes (auditoria de senhas, testes offline de força/qualidade de senhas).

WPScan

O que é: scanner de vulnerabilidades específico para WordPress.

Objetivo principal: identificar plugins/themes vulneráveis, versões desatualizadas, usuários expostos e possíveis pontos de entrada em sites WordPress.

Patator

O que é: ferramenta modular de brute-force e fuzzing (substituiu/é alternativa a várias ferramentas), altamente configurável para múltiplos protocolos.

Objetivo principal: realizar ataques automatizados (login bruteforce, fuzzing de parâmetros) com controle fino sobre retries, backoff, payloads e parsing de respostas.

## Ataques realizados 

1 - Ataque em cadeia, enumeracao smb password spraying = [/workspaces/Lab-Atack-Brute-force/Ataque em cadeia, enumeracao smb password spraying](https://github.com/dominiquelerufino-jp/Lab-Atack-Brute-force/blob/2898388910493d7bbb7cd142447a7180670c9837/Ataque%20em%20cadeia%2C%20enumeracao%20smb%20password%20spraying)

2 - Ataques de força bruta aplicados em formularios de login em sistemas web = [/workspaces/Lab-Atack-Brute-force/Ataques de força bruta aplicados em formularios de login em sistemas web](https://github.com/dominiquelerufino-jp/Lab-Atack-Brute-force/blob/2898388910493d7bbb7cd142447a7180670c9837/Ataques%20de%20for%C3%A7a%20bruta%20aplicados%20em%20formularios%20de%20login%20em%20sistemas%20web)

3 - Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux = https://github.com/dominiquelerufino-jp/Lab-Atack-Brute-force/blob/2898388910493d7bbb7cd142447a7180670c9837/Simulando%20um%20Ataque%20de%20Brute%20Force%20de%20Senhas%20com%20Medusa%20e%20Kali%20Linux


