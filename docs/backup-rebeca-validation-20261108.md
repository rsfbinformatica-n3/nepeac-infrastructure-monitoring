# Validação do backup da estação Rebeca — 2026-11-08

## Escopo sanitizado

- Cliente Bareos: `Rebeca-fd`
- Escopo autorizado: perfil Windows de trabalho da estação Rebeca
- FileSet: `Rebeca-Perfil`
- Junctions e reparse points de compatibilidade foram excluídos para evitar recursão fora do perfil.
- Nenhum agendamento automático foi habilitado.

## Evidências

- JEV aprovou o backup de teste e a progressão para o Full.
- Job de teste: status `OK`, 3 entradas de catálogo, 1.201.758 bytes, 0 erros.
- Restauração do teste: status `OK`, 2 arquivos, hashes SHA-256 e metadados aplicáveis coincidentes.
- Job Full: `13`, status `OK`, duração `02:54:46`.
- Full: 91.683 arquivos, 110.819.421.993 bytes, 0 erros FD não fatais e 0 erros SD.
- VSS ativo; autenticação Director–FD usando TLS 1.3.
- Volumes utilizados: três volumes do pool de Full do Storage Portable.
- Restauração amostral pós-Full: Job `14`, status `OK`, 2 arquivos, 1.201.758 bytes, hashes coincidentes.
- Artefatos temporários de restauração foram removidos sem sobrescrever arquivos originais.

## Estado do Storage

- Storage Portable permaneceu montado e operacional.
- Após o Full, aproximadamente 1,4 TB permaneciam livres.
- Jobs, pools, retenção e backups anteriores não foram alterados.
- Não houve reinício de Windows, Director, Storage ou PostgreSQL.

## Monitoramento

- O relatório Roberto foi ajustado para selecionar o último backup (`Type=B`) em vez de uma restauração posterior como resumo principal.
- O inventário sanitizado passou a mapear a estação ao cliente `Rebeca-fd`.
- Execução do monitor validada; mensagem Telegram aceita com `message_id` registrado somente no estado operacional protegido.
- Backup root-only do monitoramento criado antes da alteração.

## Decisão

A estação está tecnicamente apta para entrar na rotina semanal. O agendamento incremental semanal permanece desabilitado e requer ativação explícita posterior.

## Privacidade e publicação

Este documento não contém credenciais, tokens, endereços IP, nomes de arquivos pessoais, conteúdo de arquivos ou dados de usuário. Foi publicado no repositório de infraestrutura cujo remoto e branch foram verificados antes do push. O repositório é público; por isso, somente evidências sanitizadas foram incluídas.
