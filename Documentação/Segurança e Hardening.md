# Segurança e Hardening - Rede Empresarial

**A Rede do Projeto tem sua segurança feita em camadas, o objetivo é garantir que o gerenciamento remoto seja seguro, as senhas sigam padrões de força, serviços desnecessários não sejam usados, as redes não possam se comunicar entre si e sejam isoladas, o acesso remoto tenha tempo de duração seguro, proteção contra Brute Force e o acesso só seja permitido por quem seja autorizado.**

- Tudo isso é feito através de uma Stack de configurações, tecnologias e políticas, no documento passarei uma a uma para ser didático e claro, todas as configurações são aplicadas em todos os roteadores e switches da rede empresarial.

### ACLs

[ACL Departamento de TI](/Images/ACL1.png) - A ACL do Departamento de T.I visa permitir o acesso as redes internas para troubleshooting, acesso remoto a computadores e dispositivos de rede, a ACL bloqueia o departamento a acessar a rede de Clientes por questões legais de privacidade

[ACL Departamento de HR](/Images/ACL2.png) - O Departamento de HR não pode acessar nenhuma outra rede, uma vez que eles não realizam troubleshooting e nem deviam ter liberdade além do seu próprio setor. Por outro lado, eles podem acessar a DMZ somente via HTTP e DNS, a Internet e Responder Pings e Estabelecer TCP com o T.I, somente responder, nunca iniciar.

[ACL Departamento Financeiro](/Images/ACL3.png) - O Departamento Financeiro não pode acessar nenhuma outra rede, pois também não realizam troubleshooting, nem prestam suporte, o acesso é limitado a Internet, DMZ via HTTP e DNS, e a responder solicitações de Ping e TCP do T.I, somente responder, não iniciar.

[ACL Rede de Clientes](/Images/ACL4.png) - A Rede de Clientes existe somente para a clientela que irá a empresa ter acesso a internet, portanto nenhum dos clientes pode acessar a infraestrutura da empresa, nem responder a nada que venha de dentro da empresa, só possuí acesso a sair para internet e a DMZ via HTTP e DNS.

[ACL Para Gerenciamento](/Images/ACL5.png) - Todo Roteador e Switch da empresa tem uma ACL na interface de acesso remoto que só permite departamento de T.I acessa-la.

### Padrões e Configurações de Senha

Todos os dispositivos de rede possuem senhas implementadas no acesso ao console (Modo EXEC Usuário), Modo EXEC Privilegiado e para acesso remoto via SSH. Todas elas seguindo padrões de mínimo 16 caracteres, combinação de simbolos, números e letras mausculas e minusculas, e por fim proibição de senhas com palavras de peso pessoal, como datas de nascimento ou nomes de pet.

- **Todos os Roteadores são configurados para as senhas terem no mínimo 16 Caracteres de Comprimento.**
- **Todos os Dispositivos de Rede são Configurados com senhas no acesso ao Console, Modo EXEC Privilegiado e SSH.**
- **Todas as senhas nos dispositivos seguem os devidos padrões e políticas da empresa, garantindo senhas fortes.**
- **Todas as senhas são criptografadas no arquivo de configuração, através do serviço do próprio Cisco IOS**

- Senha para Acesso ao Console: @Cc#oO%n@3532!so@zle
- Senha para Acesso Privilegiado: @E#xX%eE@3532!C@pP#6

### SSH

Os Dispositivos Intermediários são acessados remotamente através do protocolo de acesso seguro SSH, ele foi implementado com chaves RSA 2048 Bits e senhas que seguem os padrões e política de senhas da empresa.

- Usuario SSH: admin
- Senha SSH: 4A@!dD##zMm3311in

### Configurações Adicionais

Além do Hardening feito acima adiciono configurações adicionais para todos os dispositivos de rede para fortificar ainda mais a segurança de cada um deles, reuni todas elas aqui para economizar espaço no documentar e deixa-lo mais didático.

- Todos os dispositivos são configurados para deslogar o usuário após 3 minutos de inatividade em linhas de acesso.
- Os Switches e Roteadores são configurados com um Banner para alerta legal de restrição de acesso.
- Os dispositivos de Rede são configurados a aceeitar apenas senhas com 16+ caracteres.
- Switches e Roteadores bloqueiam tentativas por 10 minutos após 5 tentativas erradas dentro de 1 minuto.
- Serviços e interfaces desnecessárias são todas desativadas em Roteadores.
- ACL bloqueia qualquer departamento que não seja TI a acessar linhas SSH.

### Imagens Para Ilustrar Funcionamento.

[SSH TI -> Switch/Routers](/Images/SSH_DEMONSTRATION.png)

[SSH HR/ACC -> Switch/Routers](/Images/SSH_DEMONSTRATION2.png)

[BANNER DEMONSTRATION](/Images/BANNER_DEMONSTRATION.png)