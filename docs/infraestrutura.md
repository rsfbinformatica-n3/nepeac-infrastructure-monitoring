# Infraestrutura

## Servidor

O ambiente utiliza um servidor Ubuntu de pequeno porte, reaproveitado como nó de infraestrutura local. A máquina hospeda os serviços de observabilidade, acesso remoto, inventário e backup.

## Sistema operacional

- Ubuntu Server LTS.
- Rede cabeada como rota principal.
- Wi-Fi mantido como conectividade secundária/observada.
- Tailscale para administração privada.

## Contêineres

Os serviços principais são operados por Docker Compose, com volumes persistentes e portas administrativas controladas.

## Storage

O backup utiliza volume externo dedicado montado em caminho fixo. Há proteção para evitar escrita acidental no disco raiz se o volume externo não estiver montado.
