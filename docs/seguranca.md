# Segurança

## Sanitização

Este repositório foi preparado para não conter dados operacionais sensíveis.

Itens excluídos:

- tokens e chaves API;
- senhas;
- arquivos `.env`;
- bancos SQLite;
- sessões Hermes;
- chaves SSH;
- chaves MOK/privadas;
- logs brutos;
- backups/dumps;
- IPs/MACs reais;
- seriais e patrimônios reais;
- dados pessoais.

## Wazuh

Wazuh foi avaliado e descartado para execução neste servidor específico por restrição de recursos. Pode ser reavaliado em arquitetura centralizada futura.
