# Manifesto pré-publicação

Data da auditoria: 2026-08-29, horário de Brasília.

## Repositório proposto

- **Proprietário**: `rsfbinformatica-n3`
- **Nome**: `nepeac-infrastructure-monitoring`
- **Descrição**: Plataforma open-source de monitoramento, observabilidade e gerenciamento remoto do NEPEAC.
- **Visibilidade aprovada para o primeiro push**: pública
- **Branch padrão**: `main`
- **Licença**: Apache License 2.0, aprovada pelo responsável

Nenhum repositório remoto foi criado. Após a aprovação, o diretório foi inicializado localmente com Git apenas para auditar o índice antes do primeiro commit.

## Arquivos candidatos ao primeiro commit

```text
.gitignore
.markdownlint-cli2.jsonc
LICENSE
MANIFEST.md
README.md
SECURITY.md
backup/README.md
docs/architecture.md
docs/content-plan.md
docs/licensing.md
docs/site-publication.md
examples/README.md
grafana/README.md
hermes/README.md
meshcentral/README.md
scripts/README.md
uptime-kuma/README.md
zabbix/README.md
```

## Conteúdo excluído

As seguintes classes não podem entrar no repositório:

- senhas, tokens, chaves e cookies
- arquivos `.env` e diretórios de credenciais
- chaves SSH e certificados privados
- bancos de dados, dumps e arquivos persistentes
- backups e arquivos compactados
- logs, sessões e caches
- configurações de produção
- endereços internos e identificadores únicos
- números de série e dados pessoais
- dados reais de hosts, monitores, agentes e dispositivos

## Validações do candidato

- scanner próprio: 18 arquivos, zero achados
- `detect-secrets`: zero achados no índice exportado
- `markdownlint-cli2` 0.23.2: zero problemas em 15 arquivos Markdown
- Mermaid CLI: dois diagramas renderizados com sucesso
- links internos: verificação automatizada obrigatória antes do commit
- `git diff --cached --check`: verificação obrigatória antes do commit
- revisão independente de segurança e conteúdo: obrigatória antes do commit

A auditoria deve ser repetida sobre o índice Git depois da aprovação e antes do primeiro commit. Nenhum comando de inclusão ampla, como `git add .`, será usado.

## Proposta do site

A alteração do site está preparada em uma área separada e não integra este manifesto. Ela adiciona o projeto NEPEAC e remove links de todos os cards privados. Projetos privados exibem a mensagem: “Projeto privado. Acesso ao repositório não disponível.”

Nenhum arquivo do WordPress em produção foi alterado.
