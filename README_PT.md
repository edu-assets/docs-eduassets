# Documentação do eduAssets

[English](README.md) · [Visão geral do Frontend](https://github.com/edu-assets/eduAssets/blob/main/frontend.md) · [Visão geral do Backend](https://github.com/edu-assets/eduAssets/blob/main/backend.md)

Este repositório é a fonte central da documentação do eduAssets, compartilhada pelo frontend, backend e portfólio. Os guias de produto são mantidos em português e inglês. O painel Sobre do aplicativo mantém o catálogo e o código de apresentação em `app-eduassets`; o conteúdo Markdown fica aqui.

## Estrutura do repositório

- `public/docs/` — guias bilíngues de uso, arquitetura, API, desenvolvimento, implantação, operação e hardware, além dos manuais PDF/imagens existentes. Estes são os documentos destinados ao modal de documentação do aplicativo.
- `operations/backend/` — procedimento de recuperação para mantenedores e guias dos templates de implantação Nginx. Não fazem parte do catálogo do modal e apontam aos arquivos de configuração de exemplo no repositório backend. O runbook de recuperação não contém senhas nem URLs de conexão de produção; use-o somente com acesso autorizado ao banco de dados e janela aprovada.
- `README.md` — este guia em inglês.

O caminho `public/docs/` é intencional e mantém uma estrutura estável para o frontend. Quando este repositório for público, o app poderá carregar cada Markdown a partir de `https://raw.githubusercontent.com/edu-assets/docs-eduassets/main/public` mais o respectivo caminho `/docs/...`. Se o repositório continuar privado, navegadores não conseguem autenticar no GitHub Raw; nesse caso, use hospedagem estática pública ou mantenha o fallback local do app até configurar a hospedagem.

## Edição e publicação

1. Edite os arquivos canônicos em `public/docs/` e mantenha sincronizadas as versões em português e inglês.
2. Preserve os nomes usados por `app-eduassets/src/core/docs/registry.ts`; atualize esse catálogo ao adicionar ou renomear um documento do modal.
3. Não inclua segredos, dados pessoais de estudantes, credenciais de produção ou valores de recuperação de uso único. Em repositórios públicos, todos os arquivos e todo o histórico Git ficam legíveis.
4. O app só lê a documentação remota quando `VITE_DOCS_BASE_URL` está configurada; sem ela, usa o fallback incluído no frontend. Remova o fallback apenas após validar o carregamento remoto em produção.

Este repositório não publica nem reinicia a API, não altera a VM Oracle e não executa migrations. Os procedimentos de release do backend estão nos guias de implantação.

## Guias principais

- [Manual do Usuário](public/docs/MANUAL_USUARIO.md) · [User Manual](public/docs/USER_MANUAL.md)
- [Arquitetura](public/docs/ARQUITETURA.md) · [Architecture](public/docs/ARCHITECTURE.md)
- [Referência da API](public/docs/REFERENCIA_API.md) · [API Reference](public/docs/API_REFERENCE.md)
- [Desenvolvimento](public/docs/DESENVOLVIMENTO.md) · [Development](public/docs/DEVELOPMENT.md)
- [Implantação](public/docs/GUIA_IMPLANTACAO.md) · [Deployment](public/docs/DEPLOYMENT.md)
- [Operação e Recuperação](public/docs/OPERACAO_E_RECUPERACAO.md) · [Operations and Recovery](public/docs/OPERATIONS_AND_RECOVERY.md)
- Guias de mantenedores: [Recuperação de senha](operations/backend/ADMIN_PASSWORD_RESET_RUNBOOK.md) · [Templates Nginx (PT)](operations/backend/nginx/README_PT.md) · [Nginx templates (EN)](operations/backend/nginx/README.md)
