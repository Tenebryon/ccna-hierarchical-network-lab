# Troubleshooting

Durante a implementação do laboratório foram encontrados diferentes problemas
de conectividade, roteamento e integração com o ambiente virtual.

## HSRP Split-Active

Em algumas VLANs, os dois switches de Distribuição assumiram simultaneamente
o estado Active.

A investigação envolveu a validação da comunicação Layer 2 entre os equipamentos,
das VLANs e dos enlaces existentes entre os switches de Distribuição.

Após a correção do enlace, os estados Active e Standby foram normalizados.

## OSPF

Foram encontrados problemas relacionados à formação e estabilidade de
adjacências OSPF.

A análise envolveu:

- Interfaces participantes do processo;
- Configuração de interfaces passivas;
- Endereçamento dos enlaces /30;
- Estado das interfaces Layer 3;
- Tabela de vizinhos OSPF.

## Rota Default do ISP2

Durante os testes de conectividade externa foi identificado um next-hop incorreto
na rota default do ISP2.

A rota utilizava o próprio endereço do roteador como próximo salto.

O next-hop correto foi ajustado para:

```text
200.0.0.2
```

Após a correção, o encaminhamento para a rede externa voltou a funcionar
normalmente.

## NAT/PAT e Internet

Durante um teste de conectividade, inicialmente havia suspeita de falha no NAT.

A análise das traduções mostrou que o NAT estava funcionando corretamente,
indicando que o problema estava em outro ponto da comunicação.

Foi identificado que a interface Loopback0 do roteador INTERNET estava sem o
endereço utilizado nos testes.

Após configurar:

```text
8.8.8.8/32
```

a conectividade foi restabelecida.

## VMware e PNETLab

Durante a integração do Windows Server com o laboratório foram encontrados
problemas envolvendo as redes virtuais do VMware e as interfaces do PNETLab.

Entre os cenários investigados estiveram:

- Conflito envolvendo o endereço 192.168.50.1;
- Configuração das interfaces virtuais do VMware;
- Alteração da interface utilizada pelo PNETLab após reinicialização;
- Comunicação entre o host, PNETLab e Windows Server.

A análise das interfaces, bridges e endereçamento permitiu restabelecer a
comunicação entre o laboratório e as máquinas virtuais.
