# Next.js Completo — Capítulo 14

[⬅️ Capítulo 13 (Desenvolvimento Local)](./13-desenvolvimento-local.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Deploy na Vercel) ➡️](./15-deploy-na-vercel.md)

---

## 14. Build e Produção — o que acontece quando você publica

### O que o `npm run build` faz

Quando você roda o build, o Next.js:

1. Compila todo o TypeScript para JavaScript
2. Analisa cada página e decide como ela vai ser servida
3. Otimiza imagens, CSS e JavaScript
4. Gera os arquivos finais na pasta `.next/`

### Os três tipos de renderização

O Next.js decide automaticamente como cada página vai funcionar em produção:

**Static (Estático)**
- A página é gerada uma vez no build e servida como arquivo HTML
- Mais rápido possível — sem servidor, sem banco de dados no momento da requisição
- Exemplo: página de landing, termos de uso

**Dynamic (Dinâmico)**
- A página é gerada no servidor a cada requisição
- Necessário quando os dados mudam frequentemente ou dependem do usuário logado
- Exemplo: dashboard com dados em tempo real, perfil do aluno

**Incremental Static Regeneration (ISR)**
- Começa estático, mas regenera de tempos em tempos
- Bom para dados que mudam, mas não em tempo real
- Exemplo: página de planos da academia (muda raramente)

### Como o Next.js decide

Se sua página usa `cookies()`, `headers()`, ou dados que dependem do usuário, o Next.js automaticamente a torna dinâmica. Se não usa nada disso, pode ficar estática.

Para forçar uma página a ser sempre dinâmica:

```tsx
// page.tsx
export const dynamic = 'force-dynamic'
```

### O que vai para produção

Após o build, a pasta `.next/` contém tudo. **Você não edita nada lá.** É gerado automaticamente e ignorado pelo Git.

---

## 📌 Navegação

[⬅️ Capítulo 13 (Desenvolvimento Local)](./13-desenvolvimento-local.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Deploy na Vercel) ➡️](./15-deploy-na-vercel.md)
