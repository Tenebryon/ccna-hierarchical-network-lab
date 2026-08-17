 Enterprise Network Topology - Collapsed Core Architecture

- Visão Geral
Este repositório contém o projeto e a configuração completa de uma rede corporativa redundante baseada na arquitetura **Collapsed Core** utilizando equipamentos Cisco.

 Tecnologias e Protocolos Implementados
- Camada 2: VLANs, Trunking (802.1Q), DTP Tuning, Native VLAN Isolation (VLAN 777).
- Redundância L2: EtherChannel (LACP 802.3ad) e Rapid-PVST+ (802.1w) para alinhamento de Root Bridge.
- Redundância L3: HSRP (First Hop Redundancy Protocol) para alta disponibilidade de gateway.
- *Serviços: DHCP Server distribuído com escopos primário e secundário.
- Segurança & Gerência: SSH (RSA 1024-bit), AAA local, SVI de gerência in-band (VLAN 88).

 Topologia
![Topologia do Laboratório](images/topology.png)

 Dispositivos e Arquivos de Configuração
- configs/HQ-CORE-SW1.txt - Core Switch 1 (Primary Root / HSRP Active)
- configs/HQ-CORE-SW2.txt - Core Switch 2 (Secondary Root / HSRP Backup)
- configs/HQ-ACC-1.txt - Access Switch 1 (Prédio A)
- configs/HQ-ACC-2.txt - Access Switch 2 (Prédio B)
- configs/HQ-EDGE-R1.txt - Borda / WAN Router
