# Documentação do eduAssets

[English](README.md) · [Visão geral do Frontend](https://github.com/edu-assets/eduAssets/blob/main/frontend.md) · [Visão geral do Backend](https://github.com/edu-assets/eduAssets/blob/main/backend.md)

Este repositório é a fonte canônica da documentação do eduAssets, compartilhada pelo frontend, backend e portfólio. Os guias públicos são bilíngues. A documentação é hospedada em https://docs.eduassets.tech; o aplicativo mantém o catálogo e o leitor em app-eduassets, enquanto este repositório mantém os arquivos Markdown.

**Status do produto:** versão oficial 1.0.0, publicada em 28/10/2026. O [histórico de alterações](public/docs/CHANGELOG.md) registra a versão e os fatos históricos datados.

## Estrutura do repositório

- `public/docs/` — guias bilíngues de uso, arquitetura, API, desenvolvimento, implantação, operação e hardware, além dos manuais PDF/imagens existentes. Estes são os documentos destinados ao modal de documentação do aplicativo.
- `operations/backend/` — procedimento de recuperação para mantenedores e guias dos templates de implantação Nginx. Não fazem parte do catálogo do modal e apontam aos arquivos de configuração de exemplo no repositório backend. O runbook de recuperação não contém senhas nem URLs de conexão de produção; use-o somente com acesso autorizado ao banco de dados e janela aprovada.
- `README.md` — este guia em inglês.

O caminho `public/docs/` é intencional e mantém nomes estáveis para os clientes. O host público canônico é https://docs.eduassets.tech, que serve os arquivos em `/docs/`. O frontend usa esse host por padrão; `VITE_DOCS_BASE_URL` pode substituir a URL-base. Se a requisição remota falhar ou retornar resposta sem sucesso, o app usa o fallback `public/docs/` incluído no frontend. A privacidade do repositório não controla o acesso aos guias públicos já hospedados.

## Edição e publicação

1. Edite os arquivos canônicos em `public/docs/` e mantenha sincronizadas as versões em português e inglês.
2. Preserve os nomes usados por `app-eduassets/src/core/docs/registry.ts`; atualize esse catálogo ao adicionar ou renomear um documento do modal.
3. Não inclua segredos, dados pessoais de estudantes, credenciais de produção ou valores de recuperação de uso único. Em repositórios públicos, todos os arquivos e todo o histórico Git ficam legíveis.
4. O app usa `https://docs.eduassets.tech` por padrão; `VITE_DOCS_BASE_URL` é uma substituição opcional da URL-base. Falha de rede ou resposta sem sucesso ativa o fallback Markdown incluído no frontend. Valide a origem hospedada antes de remover esse fallback.

Este repositório não publica nem reinicia a API, não altera a VM Oracle e não executa migrations. Os procedimentos de release do backend estão nos guias de implantação.

## Guias principais

- [Manual do Usuário](public/docs/MANUAL_USUARIO.md) · [User Manual](public/docs/USER_MANUAL.md)
- [Arquitetura](public/docs/ARQUITETURA.md) · [Architecture](public/docs/ARCHITECTURE.md)
- [Referência da API](public/docs/REFERENCIA_API.md) · [API Reference](public/docs/API_REFERENCE.md)
- [Modelo de Dados](public/docs/MODELO_DE_DADOS.md) · [Data Model](public/docs/DATA_MODEL.md)
- [Histórico de alterações](public/docs/CHANGELOG.md) · [Changelog](public/docs/CHANGELOG_EN.md) · [Roadmap](public/docs/ROADMAP.md) · [Roadmap](public/docs/ROADMAP_EN.md)
- [Desenvolvimento](public/docs/DESENVOLVIMENTO.md) · [Development](public/docs/DEVELOPMENT.md)
- [Implantação](public/docs/GUIA_IMPLANTACAO.md) · [Deployment](public/docs/DEPLOYMENT.md)
- [Hospedagem](public/docs/Hospedagem.md) · [Hosting](public/docs/Hosting.md)
- [Operação e Recuperação](public/docs/OPERACAO_E_RECUPERACAO.md) · [Operations and Recovery](public/docs/OPERATIONS_AND_RECOVERY.md)
- Guias de mantenedores: [Recuperação de senha](operations/backend/ADMIN_PASSWORD_RESET_RUNBOOK.md) · [Templates Nginx (PT)](operations/backend/nginx/README_PT.md) · [Nginx templates (EN)](operations/backend/nginx/README.md)
