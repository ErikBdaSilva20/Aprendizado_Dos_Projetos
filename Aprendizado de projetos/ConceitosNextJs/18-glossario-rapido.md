# Next.js Completo — Capítulo 18

[⬅️ Capítulo 17 (Boas Práticas)](./17-boas-praticas.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md)

---

## 18. Glossário rápido

| Termo | O que significa |
|---|---|
| **App Router** | Sistema de rotas do Next.js 13+ baseado na pasta `app/` |
| **Server Component** | Componente que roda no servidor, sem JavaScript no navegador |
| **Client Component** | Componente que roda no navegador, declarado com `'use client'` |
| **SSR (Server Side Rendering)** | A página é gerada no servidor a cada requisição |
| **SSG (Static Site Generation)** | A página é gerada uma vez no build e servida como arquivo estático |
| **ISR** | Regeneração estática incremental — estático com atualização periódica |
| **Hydration** | Processo de "ligar" os eventos e estado JavaScript numa página já renderizada pelo servidor |
| **Route Handler** | Arquivo `route.ts` que cria um endpoint de API |
| **Middleware** | Código que intercepta requisições antes de chegar na página |
| **Layout** | Componente que envolve páginas e persiste na navegação |
| **Streaming** | Técnica de enviar partes da página ao navegador conforme ficam prontas |
| **Bundle** | Arquivo JavaScript final gerado pelo build que vai para o navegador |
| **Hot Reload / Fast Refresh** | Atualização automática do navegador ao salvar arquivos durante o desenvolvimento |
| **`.next/`** | Pasta gerada pelo build — nunca edite manualmente |
| **`public/`** | Pasta para arquivos estáticos acessíveis pela URL diretamente |
| **Alias `@/`** | Atalho para importações a partir da pasta `src/` |

---

## Para continuar aprendendo

- **Documentação oficial (em inglês):** [nextjs.org/docs](https://nextjs.org/docs) — a melhor referência, muito bem escrita
- **Documentação do Supabase com Next.js:** [supabase.com/docs/guides/getting-started/quickstarts/nextjs](https://supabase.com/docs/guides/getting-started/quickstarts/nextjs)
- **Tanstack Query com Next.js:** [tanstack.com/query/latest](https://tanstack.com/query/latest)

> 💡 **Dica final:** Quando travar em algum erro, cole a mensagem de erro exata no Google entre aspas. Erros do Next.js são muito comuns e alguém já passou pela mesma situação.

---

## 📌 Navegação

[⬅️ Capítulo 17 (Boas Práticas)](./17-boas-praticas.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md)
