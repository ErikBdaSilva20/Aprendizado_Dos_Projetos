# Next.js Completo — Capítulo 2

[⬅️ Capítulo 1 (O que é Next.js)](./01-o-que-e-nextjs.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (App Router) ➡️](./03-app-router.md)

---

## 2. Como o Next.js pensa sobre páginas e rotas

### A regra de ouro

> **A estrutura de pastas É a rota da URL.**

Se você cria a pasta `app/alunos/`, a URL `/alunos` existe automaticamente.  
Se você cria `app/alunos/novo/`, a URL `/alunos/novo` existe automaticamente.

Não tem arquivo de configuração de rotas. Não tem `react-router`. A pasta vira a rota.

### Arquivos especiais dentro de cada pasta

Dentro de cada pasta de rota, o Next.js reconhece nomes específicos de arquivo:

| Arquivo | O que faz |
|---|---|
| `page.tsx` | O conteúdo da página naquela rota |
| `layout.tsx` | Estrutura que envolve a página (e todas as filhas) |
| `loading.tsx` | Tela de carregamento automática |
| `error.tsx` | Tela de erro automática |
| `not-found.tsx` | Tela de 404 |
| `route.ts` | Endpoint de API naquela rota |

### Rotas dinâmicas (com parâmetros na URL)

Quando a URL tem um ID variável, tipo `/alunos/123` ou `/alunos/456`:

```
app/
  alunos/
    [id]/           ← os colchetes indicam: esse trecho é dinâmico
      page.tsx      ← recebe o valor de 'id' como prop
```

Dentro do `page.tsx` você acessa assim:

```tsx
// app/alunos/[id]/page.tsx
export default function PaginaAluno({ params }: { params: { id: string } }) {
  // params.id vai ser '123', '456', qualquer valor da URL
  return <div>Aluno: {params.id}</div>
}
```

### Grupos de rotas (sem afetar a URL)

Você pode criar pastas que **agrupam** rotas sem aparecer na URL. Isso é útil para separar páginas autenticadas das públicas:

```
app/
  (auth)/           ← o parêntese indica: pasta de grupo, não aparece na URL
    login/
      page.tsx      → URL: /login
    cadastro/
      page.tsx      → URL: /cadastro

  (dashboard)/      ← outro grupo
    page.tsx        → URL: / (página inicial do dashboard)
    alunos/
      page.tsx      → URL: /alunos
```

Cada grupo pode ter seu próprio `layout.tsx` — por exemplo, o grupo `(dashboard)` tem o layout com sidebar e header, enquanto o `(auth)` tem layout limpo sem menu.

---

## 📌 Navegação

[⬅️ Capítulo 1 (O que é Next.js)](./01-o-que-e-nextjs.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (App Router) ➡️](./03-app-router.md)
