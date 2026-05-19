# Next.js Completo — Capítulo 8

[⬅️ Capítulo 7 (Arquivos Especiais)](./07-arquivos-especiais.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Middleware) ➡️](./09-middleware.md)

---

## 8. Route Handlers — sua mini API dentro do projeto

### O que são

No Next.js, você pode criar endpoints de API dentro do mesmo projeto, sem precisar de um servidor separado. Eles ficam em arquivos chamados `route.ts`.

```
app/
  api/
    alunos/
      route.ts    → GET /api/alunos, POST /api/alunos
    alunos/
      [id]/
        route.ts  → GET /api/alunos/:id, PUT /api/alunos/:id
```

### Como escrever um Route Handler

```ts
// app/api/alunos/route.ts

import { NextRequest, NextResponse } from 'next/server'

// Responde requisições GET em /api/alunos
export async function GET(request: NextRequest) {
  const alunos = await buscarAlunos()
  return NextResponse.json(alunos)
}

// Responde requisições POST em /api/alunos
export async function POST(request: NextRequest) {
  const body = await request.json()
  const novoAluno = await criarAluno(body)
  return NextResponse.json(novoAluno, { status: 201 })
}
```

### Quando usar Route Handlers

- Quando precisar de um webhook (ex: Stripe, WhatsApp)
- Quando precisar de lógica que não pode rodar no cliente (ex: enviar email)
- Quando precisar de um endpoint para integração com terceiros

**No seu projeto com Supabase**, você vai usar o SDK do Supabase direto nos Server Components e Client Components na maioria dos casos. Route Handlers ficam para casos específicos.

---

## 📌 Navegação

[⬅️ Capítulo 7 (Arquivos Especiais)](./07-arquivos-especiais.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Middleware) ➡️](./09-middleware.md)
