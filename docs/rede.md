# Rede

Esta documentação pública usa marcadores em vez de endereços reais.

## Segmentos

- Rede cabeada: `<WIRED_LAN_CIDR>`
- Rede Wi-Fi: `<WIFI_LAN_CIDR>`
- Acesso privado: `<TAILSCALE_NETWORK>`

## Descoberta controlada

A descoberta foi limitada a técnicas não destrutivas:

- ICMP leve;
- ARP/neighbour table;
- LLDP;
- consulta a serviços já existentes;
- HTTP/HTTPS sem autenticação;
- confirmação física posterior.

Não foram executados brute force, exploração, alteração de equipamentos ou instalação de agentes em massa.
