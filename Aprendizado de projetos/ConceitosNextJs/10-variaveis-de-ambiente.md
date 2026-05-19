# Next.js Completo — Capítulo 10

[⬅️ Capítulo 9 (Middleware)](./09-middleware.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Imagens, Fontes e Assets) ➡️](./11-imagens-fontes-assets.md)

---

## 10. Variáveis de Ambiente — segredos do projeto

### O que são

Variáveis de ambiente são informações sensíveis que você **não coloca no código** — como chaves de API, credenciais do banco, senhas. Elas ficam em arquivos separados que não vão para o Git.

### Os arquivos

```
.env.local          ← suas variáveis locais (NUNCA sobe para o Git)
.env.example        ← exemplo sem os valores reais (sobe para o Git)
.env.production     ← opcional, para valores específicos de produção
```

**Sempre adicione `.env.local` no `.gitignore`** — ele já vem lá por padrão no Next.js, mas confirme.

### A regra do prefixo `NEXT_PUBLIC_`

| Variável | Acessível onde |
|---|---|
| `MINHA_VARIAVEL` | Apenas no servidor (Server Components, Route Handlers, Middleware) |
| `NEXT_PUBLIC_MINHA_VARIAVEL` | No servidor E no navegador (Client Components) |

**Regra de segurança:** Nunca coloque chaves secretas com prefixo `NEXT_PUBLIC_`. Qualquer pessoa que abrir o DevTools do navegador vai ver.

### Exemplo para o projeto

```env
# .env.local

# Supabase — públicas (cliente pode ver, são do anon key)
NEXT_PUBLIC_SUPABASE_URL=https://xxxxxxxxxxxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

# Supabase — SECRETA (apenas servidor, nunca no cliente)
SUPABASE_SERVICE_ROLE_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

> ⚠️ A `SERVICE_ROLE_KEY` do Supabase bypassa todas as políticas RLS. **Jamais** coloque ela com `NEXT_PUBLIC_`. Use ela apenas em Route Handlers e funções server-side quando precisar de acesso administrative.

### Como acessar no código

```ts
// No servidor (Server Component, Route Handler):
const url = process.env.NEXT_PUBLIC_SUPABASE_URL
const serviceKey = process.env.SUPABASE_SERVICE_ROLE_KEY

// No cliente (Client Component):
const url = process.env.NEXT_PUBLIC_SUPABASE_URL
// process.env.SUPABASE_SERVICE_ROLE_KEY → undefined (correto! não vaza)
```

---

## 📌 Navegação

[⬅️ Capítulo 9 (Middleware)](./09-middleware.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Imagens, Fontes e Assets) ➡️](./11-imagens-fontes-assets.md)
