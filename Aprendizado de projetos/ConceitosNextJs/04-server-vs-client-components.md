# Next.js Completo — Capítulo 4

[⬅️ Capítulo 3 (App Router)](./03-app-router.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Busca de Dados) ➡️](./05-busca-de-dados.md)

---

## 4. Server Components vs Client Components

Essa é **a parte mais importante de entender no Next.js moderno**. Muita confusão acontece aqui.

### A ideia central

No Next.js com App Router, todo componente é **Server Component por padrão**.

Isso significa: ele roda no servidor, gera o HTML, e manda o HTML pronto para o navegador. O JavaScript desse componente **não vai para o navegador**.

### Quando usar cada um

**Server Component (padrão, sem nada especial)**

Use quando o componente:
- Busca dados do banco
- Acessa variáveis de ambiente secretas
- Não precisa de interação do usuário
- Não usa `useState`, `useEffect`, eventos de clique

```tsx
// Sem nenhuma declaração especial = Server Component
// app/alunos/page.tsx
export default async function PaginaAlunos() {
  // Pode buscar dados diretamente aqui, sem useEffect
  const alunos = await buscarAlunos()

  return (
    <ul>
      {alunos.map(aluno => <li key={aluno.id}>{aluno.nome}</li>)}
    </ul>
  )
}
```

**Client Component (`'use client'` no topo)**

Use quando o componente:
- Usa `useState` ou `useEffect`
- Responde a cliques, inputs, eventos do usuário
- Usa hooks do React
- Acessa `window`, `document`, `localStorage`
- Usa bibliotecas que precisam do navegador (ex: gráficos animados)

```tsx
'use client' // ← essa linha transforma em Client Component

import { useState } from 'react'

export function BotaoFavoritar({ alunoId }: { alunoId: string }) {
  const [favoritado, setFavoritado] = useState(false)

  return (
    <button onClick={() => setFavoritado(!favoritado)}>
      {favoritado ? '★ Favoritado' : '☆ Favoritar'}
    </button>
  )
}
```

### A regra prática

> **Comece sempre sem `'use client'`. Só adicione quando o Next.js reclamar que você está usando um hook ou evento.**

### Você pode misturar os dois

Um Server Component pode importar e usar um Client Component dentro dele. O contrário (Client importando Server) tem limitações — evite por enquanto.

```tsx
// page.tsx — Server Component
import { BotaoFavoritar } from './BotaoFavoritar' // Client Component

export default async function PaginaAluno() {
  const aluno = await buscarAluno()

  return (
    <div>
      <h1>{aluno.nome}</h1>
      <BotaoFavoritar alunoId={aluno.id} /> {/* Client dentro de Server: ok! */}
    </div>
  )
}
```

---

## 📌 Navegação

[⬅️ Capítulo 3 (App Router)](./03-app-router.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Busca de Dados) ➡️](./05-busca-de-dados.md)
