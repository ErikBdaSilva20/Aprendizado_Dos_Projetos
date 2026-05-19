# Next.js Completo — Capítulo 3

[⬅️ Capítulo 2 (Páginas e Rotas)](./02-paginas-e-rotas.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Server vs Client Components) ➡️](./04-server-vs-client-components.md)

---

## 3. App Router — o coração do Next.js moderno

### O que é o App Router

O Next.js tem dois "modos" de organizar rotas. O antigo se chama **Pages Router** (pasta `pages/`). O novo e atual se chama **App Router** (pasta `app/`).

**Você vai usar o App Router.** É o padrão desde o Next.js 13 e é o futuro do framework. Se você encontrar tutoriais usando a pasta `pages/`, eles podem estar desatualizados.

### Como identificar

- **App Router**: arquivos ficam em `src/app/` ou `app/`
- **Pages Router (antigo)**: arquivos ficam em `pages/`

### Por que o App Router é melhor

- Suporte nativo a **Server Components** (componentes que rodam no servidor)
- **Layouts aninhados** sem gambiarras
- **Loading states** automáticos por rota
- **Streaming** de dados (a página aparece aos poucos conforme carrega)
- Melhor performance geral

---

## 📌 Navegação

[⬅️ Capítulo 2 (Páginas e Rotas)](./02-paginas-e-rotas.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Server vs Client Components) ➡️](./04-server-vs-client-components.md)
