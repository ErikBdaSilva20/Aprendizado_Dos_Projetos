# Next.js Completo — Capítulo 7

[⬅️ Capítulo 6 (Layouts)](./06-layouts.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Route Handlers) ➡️](./08-route-handlers.md)

---

## 7. Loading, Error e Not Found — os arquivos especiais

### `loading.tsx` — tela de carregamento automática

Quando uma página está buscando dados (com `async/await`), o Next.js mostra o `loading.tsx` automaticamente enquanto espera.

```tsx
// app/alunos/loading.tsx
export default function CarregandoAlunos() {
  return (
    <div>
      {/* Um skeleton simples enquanto carrega */}
      <div className="animate-pulse bg-gray-200 h-8 w-48 rounded mb-4" />
      <div className="animate-pulse bg-gray-200 h-64 rounded" />
    </div>
  )
}
```

Você não precisa chamar esse componente em lugar nenhum. O Next.js sabe que quando `/alunos` está carregando, deve mostrar o `app/alunos/loading.tsx`.

### `error.tsx` — tela de erro automática

Se a `page.tsx` quebrar (erro de rede, banco fora, qualquer exceção), o Next.js mostra o `error.tsx` ao invés de travar tudo.

```tsx
'use client' // error.tsx PRECISA ser Client Component

export default function ErroAlunos({
  error,
  reset
}: {
  error: Error
  reset: () => void // função para tentar novamente
}) {
  return (
    <div>
      <h2>Algo deu errado ao carregar os alunos</h2>
      <p>{error.message}</p>
      <button onClick={reset}>Tentar novamente</button>
    </div>
  )
}
```

### `not-found.tsx` — página 404

Quando um aluno com aquele ID não existe, você pode chamar `notFound()` e o Next.js mostra o `not-found.tsx`:

```tsx
// app/alunos/[id]/page.tsx
import { notFound } from 'next/navigation'

export default async function PaginaAluno({ params }: { params: { id: string } }) {
  const aluno = await buscarAluno(params.id)

  if (!aluno) {
    notFound() // ← redireciona para o not-found.tsx
  }

  return <DetalhesAluno aluno={aluno} />
}
```

---

## 📌 Navegação

[⬅️ Capítulo 6 (Layouts)](./06-layouts.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Route Handlers) ➡️](./08-route-handlers.md)
