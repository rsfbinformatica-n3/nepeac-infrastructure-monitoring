# Arquitetura da plataforma

A plataforma separa coleta, visualização, gerenciamento e interação administrativa. Essa separação reduz acoplamento e permite evoluir um componente sem substituir toda a solução.

## Fluxo de monitoramento

1. O Zabbix coleta métricas e registra problemas.
2. O Grafana consulta o Zabbix e apresenta dashboards.
3. O Hermes Agent deverá consultar a API do Zabbix após a implantação da integração planejada.
4. O Telegram já funciona como canal para consultas administrativas e respostas. Os alertas inteligentes serão integrados em uma etapa planejada.

## Serviços complementares

- **Uptime Kuma**: verifica disponibilidade e latência
- **MeshCentral**: gerencia estações autorizadas remotamente
- **Tailscale**: protege o acesso às interfaces administrativas
- **UrBackup**: centralizará os backups das estações Windows quando a etapa for implantada

## Limites da documentação

Este repositório não publica topologia interna, endereços, inventário identificável, regras de firewall, credenciais ou configuração de produção. Exemplos futuros devem usar valores fictícios e passar por auditoria antes do commit.
