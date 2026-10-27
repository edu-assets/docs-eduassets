# eduAssets Documentation

[Português](README_PT.md) · [Frontend overview](https://github.com/edu-assets/eduAssets/blob/main/frontend.md) · [Backend overview](https://github.com/edu-assets/eduAssets/blob/main/backend.md)

This repository is the canonical source for eduAssets documentation shared by the frontend, backend, and portfolio. Public product guides are bilingual. The documentation is hosted at https://docs.eduassets.tech; the application keeps its catalog and reader code in app-eduassets, while this repository owns the Markdown.

## Repository layout

- `public/docs/` — bilingual product, architecture, API, development, deployment, operations, and hardware guides, plus the existing PDF/image manuals. These are the documents intended for the in-app documentation modal.
- `operations/backend/` — maintainer recovery procedure and Nginx deployment-template guides. They are outside the app’s modal catalog and refer to sample configuration files in the backend repository. The recovery guide contains no passwords or production connection strings; use it only with authorized database access and an approved recovery window.
- `README_PT.md` — this repository guide in Brazilian Portuguese.

The `public/docs/` path is intentional and keeps stable filenames for clients. The canonical public host is https://docs.eduassets.tech, serving files under `/docs/`. The frontend uses this host by default; `VITE_DOCS_BASE_URL` can override the base URL. If a remote request fails or returns a non-success response, the app uses its bundled `public/docs/` fallback. Repository privacy does not control access to the already-hosted public guides.

## Editing and release

1. Edit the canonical files in `public/docs/` and keep the Portuguese/English counterparts synchronized.
2. Preserve the filenames used by `app-eduassets/src/core/docs/registry.ts`; update that registry when adding or renaming a modal document.
3. Keep secrets, private student data, production credentials, and one-time recovery values out of this repository. Every file in a public repository is readable, including its Git history.
4. The app reads from `https://docs.eduassets.tech` by default; `VITE_DOCS_BASE_URL` is an optional base-URL override. A network failure or non-success response falls back to the bundled Markdown. Verify the hosted origin before removing that fallback.

The documentation repository does not deploy or restart the API, alter the Oracle VM, or run database migrations. Backend release procedures are documented in the deployment guides.

## Main guides

- [User Manual (English)](public/docs/USER_MANUAL.md) · [Manual do Usuário](public/docs/MANUAL_USUARIO.md)
- [Architecture](public/docs/ARCHITECTURE.md) · [Arquitetura](public/docs/ARQUITETURA.md)
- [API Reference](public/docs/API_REFERENCE.md) · [Referência da API](public/docs/REFERENCIA_API.md)
- [Data Model](public/docs/DATA_MODEL.md) · [Modelo de Dados](public/docs/MODELO_DE_DADOS.md)
- [Changelog](public/docs/CHANGELOG_EN.md) · [Histórico de alterações](public/docs/CHANGELOG.md) · [Roadmap](public/docs/ROADMAP_EN.md) · [Roteiro](public/docs/ROADMAP.md)
- [Development](public/docs/DEVELOPMENT.md) · [Desenvolvimento](public/docs/DESENVOLVIMENTO.md)
- [Deployment](public/docs/DEPLOYMENT.md) · [Implantação](public/docs/GUIA_IMPLANTACAO.md)
- [Hosting](public/docs/Hosting.md) · [Hospedagem](public/docs/Hospedagem.md)
- [Operations and Recovery](public/docs/OPERATIONS_AND_RECOVERY.md) · [Operação e Recuperação](public/docs/OPERACAO_E_RECUPERACAO.md)
- Maintainer guides: [Password recovery](operations/backend/ADMIN_PASSWORD_RESET_RUNBOOK.md) · [Nginx templates (EN)](operations/backend/nginx/README.md) · [Nginx templates (PT)](operations/backend/nginx/README_PT.md)
