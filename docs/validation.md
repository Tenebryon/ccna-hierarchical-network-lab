# Validação da Infraestrutura

Após a implementação foram realizados testes para verificar o funcionamento
dos principais protocolos e serviços do laboratório.

## VLANs e Trunks

Comandos utilizados:

```text
show vlan brief
show interfaces trunk
```

Validações realizadas:

- VLANs criadas;
- Portas Access associadas corretamente;
- Enlaces trunk operacionais;
- Native VLAN configurada.

## STP

Comandos utilizados:

```text
show spanning-tree
show spanning-tree root
```

Foi verificada a eleição dos equipamentos principais e secundários nas camadas
de Distribuição e Core.

## EtherChannel

Comando utilizado:

```text
show etherchannel summary
```

Foi validado o Port-Channel 1 entre SW-CORE-01 e SW-CORE-02 utilizando LACP.

## HSRP

Comando utilizado:

```text
show standby brief
```

Foram verificados:

- Virtual IP;
- Equipamento Active;
- Equipamento Standby;
- Prioridades configuradas;
- Funcionamento da redundância de gateway.

## OSPF

Comandos utilizados:

```text
show ip ospf neighbor
show ip route ospf
show ip protocols
```

Foram verificadas as adjacências OSPF e as rotas aprendidas dinamicamente.

## DHCP

No Windows Server foram verificados os escopos configurados para as VLANs do
laboratório.

Nos clientes, a validação pode ser realizada com:

```text
ipconfig /all
```

Foi confirmada a obtenção de endereços através do servidor DHCP centralizado.

## DNS

A resolução de nomes foi validada utilizando:

```text
nslookup
ping
```

O servidor DNS utilizado pelo laboratório é:

```text
192.168.50.10
```

## NAT/PAT

Nos roteadores de borda foram utilizados:

```text
show ip nat translations
show ip nat statistics
```

Foi verificada a tradução dos endereços das redes internas para os endereços
das interfaces externas.

## Conectividade Externa

O principal teste fim a fim foi realizado utilizando:

```text
ping 8.8.8.8
```

O teste valida o caminho:

```text
Host
↓
Gateway HSRP
↓
Distribuição
↓
Core
↓
ISP
↓
NAT/PAT
↓
INTERNET
```
