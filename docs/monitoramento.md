# Monitoramento

## Camadas

- Zabbix: infraestrutura, métricas e disponibilidade.
- Uptime Kuma: checks simples de endpoints e painéis.
- Grafana: visualização.
- Roberto: resumo operacional e comunicação.

## Relatórios

Os relatórios do Roberto devem ser curtos, focados em estado operacional e pendências. Alertas críticos devem ser separados dos relatórios periódicos e protegidos por deduplicação/cooldown.

## Estados

- Concluído: implantado e validado para uso.
- Em validação: implantado, mas ainda aguardando piloto ou confirmação.
- Planejado: previsto, não implantado.
