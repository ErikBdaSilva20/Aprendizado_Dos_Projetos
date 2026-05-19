# Next.js Completo — Capítulo 16

[⬅️ Capítulo 15 (Deploy na Vercel)](./15-deploy-na-vercel.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Boas Práticas) ➡️](./17-boas-praticas.md)

---

## 16. Erros comuns e como evitar

### ❌ Usar hooks em Server Components

```tsx
// ERRADO — vai quebrar
export default async function Pagina() {
  const [valor, setValor] = useState('') // ← hooks não existem em Server Components
  ...
}

// CORRETO — adicionar 'use client' ou mover o estado para um Client Component filho
'use client'
export default function Pagina() {
  const [valor, setValor] = useState('')
  ...
}
```

### ❌ Acessar `window` ou `document` no servidor

```tsx
// ERRADO — window não existe no servidor
export default function Pagina() {
  const largura = window.innerWidth // ← quebra no servidor
}

// CORRETO — dentro de useEffect (que só roda no cliente) ou verificar
useEffect(() => {
  const largura = window.innerWidth // ← seguro aqui
}, [])
```

### ❌ Importar um pacote de cliente em um Server Component

Algumas bibliotecas (ex: bibliotecas de gráficos com animação, libs que usam `window`) só funcionam no cliente. Se você importar em um Server Component, vai quebrar.

**Solução:** crie um Client Component que usa a biblioteca e importe esse componente no Server Component.

### ❌ Esquecer o `await` em Server Components

```tsx
// ERRADO — dados não vão estar disponíveis
export default async function Pagina() {
  const alunos = buscarAlunos() // ← esqueceu o await
  return <Lista itens={alunos} /> // alunos é uma Promise, não um array
}

// CORRETO
export default async function Pagina() {
  const alunos = await buscarAlunos() // ← correto
  return <Lista itens={alunos} />
}
```

### ❌ Passar objetos não serializáveis de Server para Client Components

Server Components e Client Components se comunicam por props. Essas props precisam ser serializáveis (convertíveis para JSON).

```tsx
// ERRADO — funções não são serializáveis
<ClientComponent onAction={() => console.log('oi')} /> // ← pode dar warning

// CORRETO — defina a função dentro do Client Component
```

### ❌ Colocar o `QueryClientProvider` dentro de um Server Component sem `'use client'`

```tsx
// ERRADO — QueryClientProvider é um Client Component
// Se o arquivo que o usa não tem 'use client', vai quebrar

// CORRETO — crie um arquivo separado para o Provider
// components/providers/QueryProvider.tsx
'use client'

import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
import { useState } from 'react'

export function QueryProvider({ children }: { children: React.ReactNode }) {
  const [queryClient] = useState(() => new QueryClient())
  return <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>
}
```

---

## 📌 Navegação

[⬅️ Capítulo 15 (Deploy na Vercel)](./15-deploy-na-vercel.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Boas Práticas) ➡️](./17-boas-praticas.md)
