# Plano de Endereçamento

Este documento reúne o endereçamento utilizado na infraestrutura do laboratório.

## VLANs

| VLAN |     Nome    |       Rede       |               Finalidade               |
| ---  |     ---     |       ---        |                   ---                  |
| 10   | LAB-GRIF    | 192.168.10.0/24  | Laboratórios GRIF                      |
| 20   | LAB-SONS    | 192.168.20.0/24  | Laboratórios SONS                      |
| 30   | LAB-CORV    | 192.168.30.0/24  | Laboratórios CORV                      |
| 40   | LAB-LUFA    | 192.168.40.0/24  | Laboratórios LUFA                      |
| 50   | DC          | 192.168.50.0/24  | Data Center                            |
| 60   | SAL-PRO     | 192.168.60.0/24  | Sala dos Professores                   |
| 70   | SAL-ADM     | 192.168.70.0/24  | Área Administrativa                    |
| 80   | DOR-GRIF    | 192.168.80.0/24  | Dormitório GRIF                        |
| 90   | DOR-SONS    | 192.168.90.0/24  | Dormitório SONS                        |
| 100  | DOR-CORV    | 192.168.100.0/24 | Dormitório CORV                        |
| 110  | DOR-LUFA    | 192.168.110.0/24 | Dormitório LUFA                        |
| 120  | GER-AC-DST  | 172.16.120.0/24  | Gerenciamento de Acesso e Distribuição |
| 130  | GER-DC-CORE | 172.16.130.0/24  | Gerenciamento de Core e Data Center    |
| 333  | Native      |        —         | Native VLAN dos enlaces trunk          |

## Padrão de Gateway

Nas VLANs atendidas pelos switches de Distribuição:

|     Função   | Endereço    |
|      ---     |      ---    | 
| Gateway HSRP | 192.168.X.1 |
| SW-DIST-01   | 192.168.X.2 |
| SW-DIST-02   | 192.168.X.3 |

Para a VLAN 50:

|   Equipamento  |    Endereço   |
|       ---      |      ---      |
| Gateway HSRP   | 192.168.50.1  |
| SW-CORE-01     | 192.168.50.2  |
| SW-CORE-02     | 192.168.50.3  |
| Windows Server | 192.168.50.10 |

## Gerenciamento

### VLAN 120

| Equipamento |   Endereço    |
|    ---      |      ---      |
| SW-LAB-01   | 172.16.120.10 |
| SW-LAB-02   | 172.16.120.11 |
| SW-LAB-03   | 172.16.120.12 |
| SW-LAB-04   | 172.16.120.13 |
| SW-LAB-05   | 172.16.120.14 |
| SW-LAB-06   | 172.16.120.15 |
| SW-LAB-07   | 172.16.120.16 |
| SW-LAB-08   | 172.16.120.17 |
| SW-LAB-09   | 172.16.120.18 |
| SW-LAB-10   | 172.16.120.19 |
| SW-LAB-11   | 172.16.120.20 |
| SW-LAB-12   | 172.16.120.21 |
| SW-SP-01    | 172.16.120.22 |
| SW-ADM-01   | 172.16.120.23 |
| SW-DOR-GRIF | 172.16.120.24 |
| SW-DOR-SONS | 172.16.120.25 |
| SW-DOR-CORV | 172.16.120.26 |
| SW-DIST-01  | 172.16.120.27 |
| SW-DIST-02  | 172.16.120.28 |
| SW-DOR-LUFA | 172.16.120.29 |

### VLAN 130

| Equipamento |    Endereço   |
|     ---     |      ---      |
| SW-CORE-01  | 172.16.130.10 |
| SW-CORE-02  | 172.16.130.11 |
| SW-DC-01    | 172.16.130.12 |

## Enlaces Layer 3

| Origem | Destino | Rede | IP Origem | IP Destino |
|---|---|---|---|---|
| SW-DIST-01 | SW-CORE-01 | 10.12.0.0/30  | 10.12.0.1  | 10.12.0.2  |
| SW-DIST-01 | SW-CORE-02 | 10.11.0.0/30  | 10.11.0.1  | 10.11.0.2  |
| SW-DIST-02 | SW-CORE-01 | 10.21.0.0/30  | 10.21.0.1  | 10.21.0.2  |
| SW-DIST-02 | SW-CORE-02 | 10.22.0.0/30  | 10.22.0.1  | 10.22.0.2  |
| SW-CORE-01 | ISP1       | 10.66.0.0/30  | 10.66.0.2  | 10.66.0.1  |
| SW-CORE-02 | ISP2       | 10.77.0.0/30  | 10.77.0.2  | 10.77.0.1  |
| ISP1       | INTERNET   | 200.10.0.0/30 | 200.10.0.1 | 200.10.0.2 |
| ISP2       | INTERNET   | 200.0.0.0/30  | 200.0.0.1  | 200.0.0.2  |

## Rede Externa

O roteador INTERNET utiliza:

```text
Loopback0: 8.8.8.8/32