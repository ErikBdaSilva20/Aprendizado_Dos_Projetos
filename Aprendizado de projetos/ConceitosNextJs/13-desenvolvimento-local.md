# Next.js Completo — Capítulo 13

[⬅️ Capítulo 12 (Metadata e SEO)](./12-metadata-e-seo.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Build e Produção) ➡️](./14-build-e-producao.md)

---

## 13. Desenvolvimento Local — o dia a dia

### Iniciando o projeto

```bash
# Cria um novo projeto Next.js com TypeScript, Tailwind e App Router
npx create-next-app@latest nome-do-projeto

# Entra na pasta
cd nome-do-projeto

# Inicia o servidor de desenvolvimento
npm run dev
```

O servidor sobe em `http://localhost:3000` por padrão.

### O hot reload

Quando você salva um arquivo, o Next.js atualiza o navegador automaticamente. Isso funciona para:
- Mudanças de UI: atualiza só o componente alterado (Fast Refresh)
- Mudanças de lógica: recarrega a página

### A estrutura inicial do projeto

```
meu-projeto/
├── src/
│   ├── app/
│   │   ├── layout.tsx       ← layout raiz
│   │   ├── page.tsx         ← página inicial (/)
│   │   └── globals.css      ← CSS global
│   └── components/
├── public/                  ← arquivos estáticos
├── next.config.ts           ← configurações do Next.js
├── tailwind.config.ts       ← configurações do Tailwind
├── tsconfig.json            ← configurações do TypeScript
├── package.json
└── .env.local               ← suas variáveis de ambiente (não vai pro Git)
```

### Aliases de importação (`@/`)

O Next.js configura automaticamente o alias `@/` apontando para a pasta `src/`. Isso evita imports com `../../../`:

```tsx
// ❌ Sem alias — confuso e frágil
import { Button } from '../../../components/ui/button'

// ✅ Com alias — sempre a partir da raiz do projeto
import { Button } from '@/components/ui/button'
```

### Comandos que você vai usar todo dia

```bash
npm run dev      # Inicia o servidor de desenvolvimento
npm run build    # Gera a versão de produção
npm run start    # Inicia o servidor com a build de produção (para testar localmente)
npm run lint     # Verifica erros de código com ESLint
```

### Inspecionando erros

- Erros de Server Components aparecem **no terminal** onde o `npm run dev` está rodando
- Erros de Client Components aparecem **no console do navegador** (F12)
- Erros de compilação TypeScript aparecem **no terminal** e **no editor**

---

## 📌 Navegação

[⬅️ Capítulo 12 (Metadata e SEO)](./12-metadata-e-seo.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Build e Produção) ➡️](./14-build-e-producao.md)
