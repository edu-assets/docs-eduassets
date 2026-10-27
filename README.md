# eduAssets Documentation

[Português](README_PT.md) · [Frontend overview](https://github.com/edu-assets/eduAssets/blob/main/frontend.md) · [Backend overview](https://github.com/edu-assets/eduAssets/blob/main/backend.md)

This repository is the central source for the eduAssets documentation, shared by the frontend, backend, and portfolio. Product guides are maintained in English and Portuguese. The application’s About panel keeps its catalog and presentation code in `app-eduassets`; the Markdown content lives here.

## Repository layout

- `public/docs/` — bilingual product, architecture, API, development, deployment, operations, and hardware guides, plus the existing PDF/image manuals. These are the documents intended for the in-app documentation modal.
- `operations/backend/` — maintainer recovery procedure and Nginx deployment-template guides. They are outside the app’s modal catalog and refer to sample configuration files in the backend repository. The recovery guide contains no passwords or production connection strings; use it only with authorized database access and an approved recovery window.
- `README_PT.md` — this repository guide in Brazilian Portuguese.

The `public/docs/` path is intentional: it gives the frontend a stable file layout. Once this repository is public, the app can load a Markdown file from `https://raw.githubusercontent.com/edu-assets/docs-eduassets/main/public` plus its `/docs/...` path. If the repository remains private, browsers cannot authenticate to GitHub Raw; use a public static host or keep the app’s local documentation fallback until hosting is configured.

## Editing and release

1. Edit the canonical files in `public/docs/` and keep the Portuguese/English counterparts synchronized.
2. Preserve the filenames used by `app-eduassets/src/core/docs/registry.ts`; update that registry when adding or renaming a modal document.
3. Keep secrets, private student data, production credentials, and one-time recovery values out of this repository. Every file in a public repository is readable, including its Git history.
4. The app reads remote documentation only when `VITE_DOCS_BASE_URL` is configured; otherwise it continues to use its bundled fallback. The fallback should be removed only after remote loading has been verified in production.

The documentation repository does not deploy or restart the API, alter the Oracle VM, or run database migrations. Backend release procedures are documented in the deployment guides.

## Main guides

- [User Manual (English)](public/docs/USER_MANUAL.md) · [Manual do Usuário](public/docs/MANUAL_USUARIO.md)
- [Architecture](public/docs/ARCHITECTURE.md) · [Arquitetura](public/docs/ARQUITETURA.md)
- [API Reference](public/docs/API_REFERENCE.md) · [Referência da API](public/docs/REFERENCIA_API.md)
- [Development](public/docs/DEVELOPMENT.md) · [Desenvolvimento](public/docs/DESENVOLVIMENTO.md)
- [Deployment](public/docs/DEPLOYMENT.md) · [Implantação](public/docs/GUIA_IMPLANTACAO.md)
- [Operations and Recovery](public/docs/OPERATIONS_AND_RECOVERY.md) · [Operação e Recuperação](public/docs/OPERACAO_E_RECUPERACAO.md)
- Maintainer guides: [Password recovery](operations/backend/ADMIN_PASSWORD_RESET_RUNBOOK.md) · [Nginx templates (EN)](operations/backend/nginx/README.md) · [Nginx templates (PT)](operations/backend/nginx/README_PT.md)
