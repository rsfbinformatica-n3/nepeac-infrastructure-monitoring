# Infraestrutura e Monitoramento — NEPEAC

Este repositório documenta uma implantação real de infraestrutura, observabilidade, inventário técnico e proteção de dados realizada em um ambiente institucional de pequeno porte.

O objetivo é registrar uma arquitetura pragmática, reproduzível e auditável, usando ferramentas abertas e serviços leves para operar monitoramento, acesso remoto, inventário e backup com baixo custo operacional.

> Esta versão é pública/sanitizada. Endereços, identificadores, seriais, patrimônios, tokens, credenciais, sessões, bancos e dados reais foram removidos ou substituídos por marcadores.

## Contexto

O projeto parte de um servidor Ubuntu existente, reaproveitado como nó local de infraestrutura. A solução foi construída com foco em:

- observabilidade de serviços e rede;
- documentação técnica atualizável;
- inventário progressivo de ativos;
- backup centralizado com validação por restore;
- alertas e relatórios operacionais por Telegram;
- operação segura, sem varreduras agressivas e sem exposição de segredos.

## Arquitetura resumida

```mermaid
flowchart TB
    subgraph Rede_Local["Rede local institucional"]
        Switch["Switch de acesso"]
        Gateway["Gateway/Firewall"]
        AP["Wi-Fi/APs"]
        Endpoints["Desktops, notebooks e impressoras"]
    end

    subgraph <MONITORING_SERVER>["Servidor <MONITORING_SERVER> - Ubuntu Server"]
        Docker["Docker Compose"]
        Zabbix["Zabbix"]
        Grafana["Grafana"]
        Kuma["Uptime Kuma"]
        Mesh["MeshCentral"]
        UrBackup["UrBackup Server"]
        Roberto["Hermes Agent / Roberto"]
        Inventory["Inventário estruturado"]
    end

    subgraph Backup["Storage externo dedicado"]
        BackupDisk["<BACKUP_STORAGE_PATH>"]
    end

    subgraph Operacao["Operação"]
        Telegram["Telegram"]
        Admin["Acesso privado via VPN mesh"]
    end

    Endpoints --> Switch
    AP --> Switch
    Switch --> Gateway
    Switch --> <MONITORING_SERVER>
    Docker --> Zabbix
    Docker --> Grafana
    Docker --> Kuma
    Docker --> Mesh
    Docker --> UrBackup
    UrBackup --> BackupDisk
    Zabbix --> Roberto
    Kuma --> Roberto
    UrBackup --> Roberto
    Inventory --> Roberto
    Roberto --> Telegram
    Admin --> <MONITORING_SERVER>
```

## Tecnologias

- **Ubuntu Server** como base operacional.
- **Docker Compose** para orquestração local dos serviços.
- **Zabbix** para monitoramento de infraestrutura.
- **Grafana** para visualização de métricas.
- **Uptime Kuma** para checks simples de disponibilidade.
- **MeshCentral** para gestão remota, em configuração controlada.
- **Tailscale** para acesso privado administrativo.
- **UrBackup** para backup centralizado em storage dedicado.
- **Hermes Agent / Roberto** para relatórios e interpretação operacional.
- **Inventário JSON/CSV/Markdown** como fonte determinística de documentação.

## Monitoramento e Roberto

Roberto é o agente operacional responsável por consolidar dados de fontes determinísticas e comunicar o estado do ambiente. Ele não é a fonte da verdade: interpreta informações vindas de Zabbix, Uptime Kuma, UrBackup, métricas locais e inventário estruturado.

Os relatórios programados foram desenhados para serem curtos e acionáveis, evitando ruído. Alertas críticos permanecem separados e devem usar deduplicação/cooldown.

## Backup

O UrBackup Server foi preparado para gravar em um storage externo montado de forma controlada. A implantação inclui proteção para evitar que backups sejam gravados no disco raiz caso o volume de backup não esteja montado.

Status público do backup:

- servidor preparado: concluído;
- storage dedicado: em validação;
- piloto Windows com restore e hash: pendente.

## Inventário

O inventário é mantido em estrutura determinística e atualizável. A descoberta de ativos utiliza fontes passivas ou controladas, como LLDP, ARP/neighbour table, ICMP leve, serviços já existentes e confirmação física posterior.

Esta versão pública inclui apenas exemplos sanitizados em `inventory/`.

## Segurança

A publicação deste repositório não inclui:

- credenciais;
- tokens;
- bancos de dados;
- logs brutos;
- sessões Hermes;
- chaves SSH;
- chaves MOK;
- seriais/patrimônios reais;
- IPs/MACs reais;
- dados de usuários ou estações.

## Status atual

### Concluído

- base Ubuntu Server em operação;
- stack Docker Compose implantada;
- Zabbix implantado;
- Grafana implantado;
- Uptime Kuma implantado;
- UrBackup Server implantado;
- documentação inicial da rede e inventário;
- descoberta controlada inicial de redes cabeada e Wi-Fi;
- Roberto/Hermes Agent operando como camada de relatório.

### Em validação

- MeshCentral: serviço implantado, configuração operacional final em validação;
- UrBackup: piloto de backup/restore em estação Windows pendente;
- inventário: enriquecimento físico progressivo;
- sensor Wi-Fi do Roberto: driver preparado, validação final pendente.

### Planejado

- validação completa de restore com SHA-256;
- refinamento de dashboards;
- cadastro gradual de endpoints confirmados;
- relatório operacional com inventário enriquecido;
- documentação de procedimentos de manutenção.

## Wazuh

Wazuh foi avaliado como alternativa de segurança/SIEM/XDR, mas não foi implantado neste host. A decisão técnica foi descartar a instalação local por limitação de recursos disponíveis, mantendo a possibilidade de uma arquitetura centralizada em outro servidor/VM no futuro.

## Roadmap

1. Concluir piloto UrBackup com restore real.
2. Confirmar fisicamente ativos pendentes do inventário.
3. Validar sensor Wi-Fi dedicado do Roberto.
4. Consolidar dashboards e relatórios curtos.
5. Documentar rotina de manutenção e recuperação.
6. Avaliar publicação do repositório após revisão final.
