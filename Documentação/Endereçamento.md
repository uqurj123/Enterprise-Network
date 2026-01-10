# Tabela de Endereçamento IPv4 - Projeto Rede Empresarial

## IPv4

    Nota: Para esse projeto por questões éticas represento endereços IP públicos através de privados, segue a lógica utilizada:
    
    - 10.0.0.0 -> Endereços Privados da Rede Empresarial
    - 192.168.0.0 -> Endereços Privados de Rede Doméstica
    - 172.16.0.0 -> Endereços "Públicos"


#### **Rede Empresarial**
    Endereço Utilizado 10.0.0.0/16 (255.255.0.0) - Total de 65.536 Endereços

        Departamento de TI (170 Hosts)

        - Rede: 10.0.0.0/24 (255.255.255.0)
        - Intervalo de Endereços: 10.0.0.1 - 10.0.0.254
        - Endereço de Gateway: 10.0.0.1
        - Endereço de Broadcast 10.0.0.255
        - Endereço do PC Exemplo: 10.0.0.5
        - Endereço Switch (SVI): 10.0.0.2


        Rede para Clientes (60 Hosts)

        - Rede: 10.0.1.0/26 (255.255.255.192)
        - Intervalo de Endereços: 10.0.1.1 - 10.0.1.62
        - Endereço de Gateway: 10.0.1.1
        - Endereço de Broadcast: 10.0.1.63
        - Endereço Dispositivo Exemplo: 10.0.1.6


        Departamento de RH (45 Hosts)

        - Rede: 10.0.1.64/26 (255.255.255.192)
        - Intervalo de Endereços: 10.0.1.65 - 10.0.1.126
        - Endereço de Gateway: 10.0.1.65
        - Endereço de Broadcast: 10.0.1.127
        - Endereço PC Exemplo: 10.0.1.70
        - Endereço Switch (SVI): 10.0.1.66

        Departamento Financeiro (20 Hosts)

        - Rede: 10.0.1.128/27 (255.255.255.224)
        - Intervalo de Endereços: 10.0.1.129 - 10.0.1.158
        - Endereço de Gateway: 10.0.1.129
        - Endereço de Broadcast: 10.0.1.159
        - Endereço PC Exemplo: 10.0.1.135
        - Endereço Switch (SVI): 10.0.1.130

        DMZ (Zona Desmilitarizada)

        - Rede: 10.40.0.0/24 (255.255.255.0)
        - Intervalo de Endereços: 10.40.0.1 - 10.40.0.254
        - Endereço de Gateway: 10.40.0.1
        - Endereço de Broadcast: 10.40.0.255
        - Endereço Servidor Web Localmente (HTTP e DNS): 10.40.0.10
        - Endereço Servidor Web Público (NAT 1:1): 172.16.40.10

        Infraestrutura de Routers

        - Rede: 10.0.1.160/30 (255.255.255.252)
        - Intervalo de Endereços: 10.0.1.161 - 10.0.1.162
        - Endereço de Broadcast: 10.0.1.163
        - Endereço Router-Edge: 10.0.1.161
        - Endereço Router-Distribution: 10.0.1.162
        - Rota de Router-Distribution: Via 10.0.1.161
        - Gateway de Router-Edge: ISP Link via OSPF

    Nota: Todas as redes tem design para crescimento futuro sem necessidade de reendereçamento, assim como, todos os endereços IP dos dispositivos finais (PC) vão ser atribuídos por DHCP, coloquei manual aqui para ficar didático.

#### **Rede LAN**
    
    LAN 
    - Rede: 192.168.1.0/24 (255.255.255.0)
    - Intervalo de Endereços: 192.168.1.1 - 192.168.1.254
    - Endereço de Gateway: 192.168.1.1
    - Endereço de Broadcast: 192.168.1.255
    - Endereço Dispositivo Exemplo: 192.168.1.10

#### **WAN/ISP**
    O objetivo do projeto é projetar uma rede empresarial e o domínio da ISP foge do nosso escopo, ela existe no projeto apenas para fornecer complexidade e conectividade, portanto, não vou endereça-la em tabela como fiz nas redes acima!