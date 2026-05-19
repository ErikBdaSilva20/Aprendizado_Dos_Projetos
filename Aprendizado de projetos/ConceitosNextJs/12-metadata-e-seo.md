# Next.js Completo — Capítulo 12

[⬅️ Capítulo 11 (Imagens, Fontes e Assets)](./11-imagens-fontes-assets.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Desenvolvimento Local) ➡️](./13-desenvolvimento-local.md)

---

## 12. Metadata e SEO

### Como configurar título e descrição de páginas

No App Router, você exporta um objeto `metadata` da sua `page.tsx` ou `layout.tsx`:

```tsx
// app/alunos/page.tsx
import type { Metadata } from 'next'

export const metadata: Metadata = {
  title: 'Alunos | Academia Manager',
  description: 'Gerencie os alunos da sua academia',
}

export default function PaginaAlunos() {
  return <div>...</div>
}
```

### Metadata dinâmica (baseada em dados)

Para páginas com parâmetros na URL (como o perfil de um aluno específico):

```tsx
// app/alunos/[id]/page.tsx
export async function generateMetadata({ params }: { params: { id: string } }) {
  const aluno = await buscarAluno(params.id)

  return {
    title: `${aluno.nome} | Academia Manager`,
  }
}
```

---

## 📌 Navegação

[⬅️ Capítulo 11 (Imagens, Fontes e Assets)](./11-imagens-fontes-assets.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Desenvolvimento Local) ➡️](./13-desenvolvimento-local.md)
