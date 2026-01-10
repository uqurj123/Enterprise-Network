# Visão Geral - Rede Empresarial IPv4/IPv6

*Esse documento busca apresentar de forma técnica a disposição da topologia, o motivo das configurações implementadas, como as redes se conversam e quais problemas do mundo real elas resolvem, vamos passar tópico a tópico e rede a rede, para deixar o mais didático possível.*


## Disposição de Redes no Projeto

#### **Rede Empresarial**
    A Rede da Corporação é dividida em 3 Departamentos e 1 Rede para Clientes

    - Financeiro (20 Hosts)
    - Recursos Humanos (45 Hosts)
    - TI (170 Hosts)
    - Rede de Clientes (60 Hosts)
    - DMZ (254 Hosts)

    A Rede é composta por:

    - 1 Roteador na Borda para conexão com a ISP (Enterprise-Edge-Router)
    - 1 Roteador Central para Distribuição de tráfego interno (Enterprise-Distribution-Router) 
    - 3 Switches para conectividade dos dispositivos em cada departamento
    - 1 Home Router para conectividade Wireless na Rede para Clientes
    - 1 Servidor na DMZ oferecimento de serviços Web, HTTP para internet e DNS localmente.

    Problemas que a Rede Resolve:

    - VLSM evita desperdício de endereços.
    - Segmentação correta aumenta a segurança
    - Distribution Router funcionando como servidor DHCP local promove confiabilidade e automação para endereçamento
    - Subnets permitem escalabilidade futura, tanto para mais endereços, quanto para implementação de Firewalls
    - Desempenho aumentado por conta da segmentação
    - Fácil de troubleshooting caso necessário.
    - DMZ e servidor com endereço NAT 1:1 oferece isolamento e segurança ao mesmo tempo que oferece serviços para a internet.
    - Servidor na DMZ opera com Split DNS, permitindo que clientes internos resolvam o domínio localmente.
    

#### **WAN ISP**
    
    A ISP é representada através de um core com 4 roteadores, os 4 roteadores oferecem caminhos diferentes e redundância caso um deles caia, além disso, a ISP fornece um servidor DNS público para resolução de dominíos. A lógica de roteamento implementada no projeto usa BGP + OSPF, no mundo real ISPs usam IBGP, IGP e eBGP, no projeto demonstrei com OSPF pela didática e escala menor.

    4 Roteadores - Redundância, roteamento e complexidade técnica
    1 Servidor DNS - Oferecimento de serviços para profundidade do projeto


#### **LANs Domésticas**
    Existem 1 LAN doméstica simples, o objetivo é adicionar mais complexidade técnica, demonstrando um cliente acessando serviços web da empresa, e acessando um servidor DNS da ISP.


## Conectividade Entre as Redes
Para conectividade entre as redes todos os roteadores são configurados com o protocolo OSPF, cada roteador anuncia as proprias redes que estão conectadas em sua interface ou guardadas por ele, e para representar um bloco público contratado para serviços oferecidos por servidores, o protocolo BGP é usado para anunciar qual rede possuí o intervalo.

    Roteadores configurados com OSPF: Todos com OSPF ativo e configurado, anunciando suas respectivas redes.

    Roteadores com BGP: O Roteador de borda da empresa anuncia que possuí o bloco 172.16.40.0/24 (Público em nosso exemplo), e o roteador ISP conectado a ele cria adjacência e repassa a rota via OSPF para os demais roteadores da ISP

    NAT 1:1 - Na topologia, uso NAT 1:1 para mapear um endereço especifico do meu bloco público ao servidor desejado, dando mais escalabilidade e segurança á rede.


## Limitações Técnicas e Éticas
*Só um adendo, por opções éticas eu utilizo endereços IPv4 privado para representar os públicos, uma vez que é errado usar endereços que já são escassos e reservados a empresas reais!*

*1 limitação se baseia no tamanho da ISP, uma estrutura ISP tem milhares de roteadores e uma central com switches e aparelhos variados, aqui limito por questões técnicas a uma topologia mais simples, porém o funcionammento se mantém*

*2 limitação, a rede tem limitações e carência de camadas de segurança com Firewalls, IPS e IDS, o Packet Tracer limita IPS e IDS, porém Firewall é implementado e assim que meu conhecimento técnico aumentar escalarei a rede*

*3 limitação, o Packet Tracer não permite DNS Fowarding, portanto não é possível configurar o servidor local da empresa para um outro servidor DNS caso não seja resolvido nele, é uma limitação do próprio software*

*4 limitação, o Packet Tracer não possuí funcionalidade para um Home Router oferecer fibra óptica diretamente, portanto não pude seguir o padrão atual, tive que usar conexão coaxial através de um cable modem e um Cloud-PT para transferência de tecnologia*

