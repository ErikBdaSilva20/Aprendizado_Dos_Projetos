# Next.js Completo — Capítulo 6

[⬅️ Capítulo 5 (Busca de Dados)](./05-busca-de-dados.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Arquivos Especiais) ➡️](./07-arquivos-especiais.md)

---

## 6. Layouts — a mágica da estrutura compartilhada

### O que é um layout

Um layout é um componente que **envolve** as páginas filhas e **não é recriado** quando o usuário navega entre elas.

Pensa assim: no seu dashboard, o menu lateral (sidebar) e o cabeçalho (header) aparecem em todas as páginas. Você não quer recriar esses elementos toda vez que o usuário clica em algo. O layout faz exatamente isso — ele fica fixo enquanto só o conteúdo principal muda.

### Como funciona na prática

```
app/
  layout.tsx           ← Layout raiz (envolve tudo)
  (dashboard)/
    layout.tsx         ← Layout do dashboard (sidebar + header)
    page.tsx           ← Conteúdo da home do dashboard
    alunos/
      page.tsx         ← Conteúdo da listagem de alunos
```

```tsx
// app/(dashboard)/layout.tsx
export default function DashboardLayout({
  children  // ← aqui vai o conteúdo de cada page.tsx
}: {
  children: React.ReactNode
}) {
  return (
    <div className="flex h-screen">
      <Sidebar />         {/* Sempre visível */}
      <div className="flex-1">
        <Header />        {/* Sempre visível */}
        <main>
          {children}      {/* Aqui muda conforme a rota */}
        </main>
      </div>
    </div>
  )
}
```

Quando o usuário navega de `/alunos` para `/frequencia`, o `DashboardLayout` **não remonta**. Só o `{children}` muda. Isso é muito mais performático.

### Layout raiz (obrigatório)

O `app/layout.tsx` é obrigatório e envolve absolutamente tudo. É onde você coloca as tags `<html>` e `<body>`, fontes globais, providers do Tanstack Query, etc.

```tsx
// app/layout.tsx
import { QueryProvider } from '@/components/providers/QueryProvider'

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="pt-BR">
      <body>
        <QueryProvider>
          {children}
        </QueryProvider>
      </body>
    </html>
  )
}
```

---

## 📌 Navegação

[⬅️ Capítulo 5 (Busca de Dados)](./05-busca-de-dados.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Arquivos Especiais) ➡️](./07-arquivos-especiais.md)
