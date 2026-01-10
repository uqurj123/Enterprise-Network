# Rede Empresarial - Laboratório de Redes

Esse projeto visa demonstrar uma rede Empresarial com 3 Departamentos, 1 Rede para Visitantes (Clientes) e 1 DMZ para oferecer serviços á internet, todas elas segmentadas e seguras através de ACLs, Subnetting VLSM, Hardening nos dispositivos e configurações de acesso remoto para suporte com SSH.

- A topologia acompanha uma infraestrutura ISP com roteadores e um servidor DNS dedicado, e uma LAN doméstica para demonstrar acesso aos serviços, conectividade e isolamento através do NAT, esses adendos oferecem complexidade e maior profundidade técnica ao projeto.


### Objetivos do Projeto

- Simular uma rede empresarial real.
- Aplicar Subnetting VLSM em IPv4.
- Configurar NAT nas Bordas.
- Implementar roteamento com OSPF e BGP.
- Aplicar Hardening em Dispositivos Intermediários.
- Isolar as redes aplicando segurança com ACLs.
- Demonstrar funcionamento de uma DMZ.
- Oferecer serviços Web (HTTP e DNS) através de um servidor na DMZ.
- Demonstrar amplo entendimento de topologia, rede e segurança.


### Tecnologias Utilizadas

- Cisco Packet Tracer
- Cisco Internetwork Operational System
- IPv4
- OSPF
- BGP
- NAT
- DHCP
- SSH
- TCP/IP
- Subnetting VLSM
- HTTP
- DNS
- ACL (Access Control List)
- DMZ (Demilitarized Zone)


### Estrutura do Projeto

- `README.md` - Visão teórica geral do projeto e tecnologias utilizadas
- `Documentação/Visão-Geral.md` - Visão técnica da rede, mostrando a arquitetura e engenharia utilizada
- `Documentação/Endereçamento.md` - Plano de endereçamento da rede
- `Documentação/Segurança e Hardening.md`- Explicação técnica do hardening usados nos dispositivos de rede
- `Topology/topologia.png` - Topologia ilustrada da rede
- `Packet-Tracer/rede-empresarial.pkt` - Arquivo do packet tracer com a rede configurada e funcional.


### Limitações do Projeto

O projeto tem limitações na implementação de camadas de segurança, como Firewalls, IDS, IPS e políticas, também apenas simula de forma didática o funcionamento de uma ISP, sem a complexidade real, e por questões éticas não uso endereços IPv4 e IPv6 públicos, portanto, é simulado endereços privados no lugar.


### Como Navegar para Entendimento

1. Comece pela `Visão-Geral.md`, ele dará a visão técnica e a engenharia implementada.
2. Veja o `Endereçamento.md`, ele contém tabela para entender o endereçamento de cada rede.
3. Abra o `.pkt` na pasta Packet-Tracer, aqui fica por conta explorar e entender o projeto.
4. Opcional porém educado, ver os arquivos `Segurança.md` e `topology.png`, para aprofundamento técnico e didático.