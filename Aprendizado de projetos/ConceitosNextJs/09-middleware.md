# Next.js Completo — Capítulo 9

[⬅️ Capítulo 8 (Route Handlers)](./08-route-handlers.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Variáveis de Ambiente) ➡️](./10-variaveis-de-ambiente.md)

---

## 9. Middleware — o segurança da porta

### O que é

O middleware é um código que roda **antes de qualquer requisição chegar na página**. Ele funciona como um segurança na porta: verifica se a pessoa pode entrar antes de abrir.

No seu projeto, ele vai verificar se o usuário está autenticado antes de deixar ele acessar o dashboard.

### Onde fica

O arquivo se chama `middleware.ts` e fica **na raiz do projeto** (fora da pasta `app/`):

```
src/
  app/
  middleware.ts    ← aqui
```

### Exemplo com Supabase Auth

```ts
// middleware.ts
import { createServerClient } from '@supabase/ssr'
import { NextResponse } from 'next/server'
import type { NextRequest } from 'next/server'

export async function middleware(request: NextRequest) {
  const response = NextResponse.next()

  const supabase = createServerClient(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!,
    { cookies: { /* configuração de cookies */ } }
  )

  const { data: { user } } = await supabase.auth.getUser()

  // Se não está logado e está tentando acessar o dashboard
  if (!user && request.nextUrl.pathname.startsWith('/dashboard')) {
    return NextResponse.redirect(new URL('/login', request.url))
  }

  // Se está logado e tenta acessar o login, manda para o dashboard
  if (user && request.nextUrl.pathname === '/login') {
    return NextResponse.redirect(new URL('/dashboard', request.url))
  }

  return response
}

// Define quais rotas o middleware vai interceptar
export const config = {
  matcher: ['/((?!_next/static|_next/image|favicon.ico).*)']
}
```

### O que o `matcher` faz

O matcher diz ao middleware quais URLs ele deve verificar. A expressão acima diz: "intercepte tudo, exceto arquivos estáticos do Next.js". Você não quer que o middleware rode em toda imagem e CSS, só nas páginas reais.

---

## 📌 Navegação

[⬅️ Capítulo 8 (Route Handlers)](./08-route-handlers.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Variáveis de Ambiente) ➡️](./10-variaveis-de-ambiente.md)
