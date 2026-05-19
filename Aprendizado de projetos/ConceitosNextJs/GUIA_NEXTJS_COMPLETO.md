# 🚀 Guia Next.js Completo — Do Zero ao Deploy

> **Bem-vindo ao Guia Definitivo de Next.js!**
> Este material foi planejado estrategicamente para desenvolvedores que já conhecem React e JavaScript/TypeScript, mas desejam dominar o Next.js moderno (App Router) para construir aplicações reais, rápidas e profissionais (como nosso SaaS de Academias).

Para facilitar sua leitura, evitar travamento de navegação e organizar os tópicos de forma modular, o guia foi dividido em **18 rotas/capítulos individuais**. Cada rota funciona como um módulo focado, otimizando o carregamento e permitindo que você navegue fluidamente entre os tópicos.

---

## 🗺️ Sumário e Rotas de Aprendizado

Selecione um capítulo abaixo para abrir o seu conteúdo dedicado. A navegação interna em cada arquivo permite que você avance, volte ou retorne ao índice a qualquer momento:

| Módulo / Capítulo | Descrição Técnica | Status | Link |
| :--- | :--- | :--- | :--- |
| **01. O que é Next.js e por que usar** | Diferenças entre React Puro e Next.js, problemas que ele resolve e motivações para o SaaS. | 🔥 Comece Aqui | [Abrir Capítulo](./01-o-que-e-nextjs.md) |
| **02. Páginas e Rotas** | A regra de ouro do roteamento baseado em pastas, arquivos especiais e parâmetros dinâmicos. | 📂 Estrutura | [Abrir Capítulo](./02-paginas-e-rotas.md) |
| **03. App Router** | O coração do Next.js moderno. Diferenças do Pages Router e por que é o futuro. | ⚡ Core | [Abrir Capítulo](./03-app-router.md) |
| **04. Server vs Client Components** | A regra de ouro da renderização: quando usar Server Components (padrão) e Client Components (`'use client'`). | 💡 Crucial | [Abrir Capítulo](./04-server-vs-client-components.md) |
| **05. Como o Next.js busca dados** | `async/await` no servidor (Server Components) vs Tanstack Query no cliente (Client Components). | 🔄 Dados | [Abrir Capítulo](./05-busca-de-dados.md) |
| **06. Layouts** | Estruturas compartilhadas (Header, Sidebar), layouts aninhados e o layout raiz obrigatório. | 🧱 Layout | [Abrir Capítulo](./06-layouts.md) |
| **07. Arquivos Especiais** | Feedback visual imediato com `loading.tsx`, tratamento de erros com `error.tsx` e páginas 404 com `not-found.tsx`. | ✨ UX/UI | [Abrir Capítulo](./07-arquivos-especiais.md) |
| **08. Route Handlers** | Criação de APIs robustas (`route.ts`) dentro do próprio Next.js para Webhooks, integrações e ações seguras. | 📡 API | [Abrir Capítulo](./08-route-handlers.md) |
| **09. Middleware** | Controle de acesso a rotas, proteção do dashboard e integração com Supabase Auth. | 🛡️ Segurança | [Abrir Capítulo](./09-middleware.md) |
| **10. Variáveis de Ambiente** | Arquivos `.env.local` e `.env.example`, segurança de chaves e o prefixo `NEXT_PUBLIC_`. | 🔑 Segredos | [Abrir Capítulo](./10-variaveis-de-ambiente.md) |
| **11. Imagens, Fontes e Assets** | Otimização com o componente `<Image>`, importação de fontes com `next/font` e arquivos estáticos na pasta `public/`. | 🎨 Assets | [Abrir Capítulo](./11-imagens-fontes-assets.md) |
| **12. Metadata e SEO** | Títulos e descrições estáticos vs dinâmicos (baseados em parâmetros) para otimização em motores de busca. | 🔍 SEO | [Abrir Capítulo](./12-metadata-e-seo.md) |
| **13. Desenvolvimento Local** | Dia a dia de desenvolvimento, criação do projeto com `create-next-app`, hot reload, aliases (`@/`) e comandos úteis. | 🛠️ Setup | [Abrir Capítulo](./13-desenvolvimento-local.md) |
| **14. Build e Produção** | O que o `npm run build` faz por baixo dos panos e os três tipos de renderização: Estático, Dinâmico e ISR. | 🏗️ Produção | [Abrir Capítulo](./14-build-e-producao.md) |
| **15. Deploy na Vercel** | Como fazer o deploy em minutos conectado ao GitHub, gerenciamento de ambientes e variáveis de ambiente online. | 🚀 Nuvem | [Abrir Capítulo](./15-deploy-na-vercel.md) |
| **16. Erros comuns e como evitar** | Guia de sobrevivência: hooks no servidor, acesso a `window`, imports inválidos, promessas sem await, props não serializáveis. | 🩹 Debugging | [Abrir Capítulo](./16-erros-comuns.md) |
| **17. Boas práticas gerais** | Estruturação de componentes, otimizações de performance, interfaces TypeScript e boas práticas de Git. | 🏆 Qualidade | [Abrir Capítulo](./17-boas-praticas.md) |
| **18. Glossário rápido** | Tabela rápida de termos (SSR, SSG, ISR, Hydration, Streaming, Bundle, etc.) e links úteis de aprendizado. | 📖 Dicionário | [Abrir Capítulo](./18-glossario-rapido.md) |

---

> [!TIP]
> **💡 Dica de Leitura:**
> Caso você queira ler o guia de ponta a ponta de forma linear, basta abrir o **[Capítulo 01](./01-o-que-e-nextjs.md)**. No final de cada página, você encontrará botões dedicados de navegação rápida para avançar para o próximo módulo sem precisar voltar aqui!

> [!IMPORTANT]
> **⚠️ Sobre os Links no Markdown Reader / VS Code:**
> Ao clicar nos links da tabela acima, o seu Markdown Reader (ou o editor de Markdown do VS Code) abrirá diretamente o arquivo correspondente de forma instantânea. Isso resolve o problema de links que "não navegam" ao clicar no sumário devido ao slugify de caracteres especiais!

---

[⬅️ Voltar para o Mapa de Conhecimento Central](../MAPA_DE_CONHECIMENTO.md)
