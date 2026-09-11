# Backup

## Objetivo

Centralizar backup de estações selecionadas para storage dedicado, com prova de restauração.

## UrBackup

O UrBackup Server foi implantado para receber backups de clientes autorizados. O servidor só deve operar quando o destino de backup dedicado estiver montado e validado.

## Critério de sucesso

Um backup só é considerado validado após:

1. backup real de arquivos de teste;
2. restauração para diretório separado;
3. comparação de hashes SHA-256 entre original e restaurado.

O piloto de restore ainda está pendente nesta versão do projeto.
