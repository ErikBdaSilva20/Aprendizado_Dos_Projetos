# Next.js Completo — Capítulo 5

[⬅️ Capítulo 4 (Server vs Client Components)](./04-server-vs-client-components.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Layouts) ➡️](./06-layouts.md)

---

## 5. Como o Next.js busca dados

### No Server Component: direto, sem cerimônia

Você pode usar `async/await` diretamente na função do componente:

```tsx
// Isso funciona porque page.tsx é um Server Component
export default async function PaginaAlunos() {
  const response = await fetch('https://sua-api.com/alunos')
  const alunos = await response.json()

  return <ListaAlunos alunos={alunos} />
}
```

Ou com Supabase:

```tsx
export default async function PaginaAlunos() {
  const { data: alunos } = await supabase
    .from('alunos')
    .select('*')
    .eq('academia_id', academiaId)

  return <ListaAlunos alunos={alunos} />
}
```

### No Client Component: com Tanstack Query

Em Client Components (que têm interatividade), você usa o **Tanstack Query** como definido nos agentes:

```tsx
'use client'

import { useQuery } from '@tanstack/react-query'

export function ListaAlunos() {
  const { data: alunos, isLoading } = useQuery({
    queryKey: ['alunos'],
    queryFn: () => alunoService.listar()
  })

  if (isLoading) return <p>Carregando...</p>
  return <ul>{alunos?.map(a => <li key={a.id}>{a.nome}</li>)}</ul>
}
```

### Quando usar cada abordagem

| Situação | Abordagem |
|---|---|
| Dados que existem quando a página carrega (sem interação) | Server Component com async/await |
| Dados que mudam com base em ação do usuário (filtro, busca) | Client Component + Tanstack Query |
| Dados que precisam atualizar em tempo real | Client Component + Tanstack Query |
| Dashboard inicial com métricas | Server Component (carrega mais rápido) |

---

## 📌 Navegação

[⬅️ Capítulo 4 (Server vs Client Components)](./04-server-vs-client-components.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Layouts) ➡️](./06-layouts.md)
