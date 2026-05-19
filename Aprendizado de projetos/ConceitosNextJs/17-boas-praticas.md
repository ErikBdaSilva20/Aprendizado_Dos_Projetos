# Next.js Completo — Capítulo 17

[⬅️ Capítulo 16 (Erros Comuns)](./16-erros-comuns.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Glossário Rápido) ➡️](./18-glossario-rapido.md)

---

## 17. Boas práticas gerais

### Organização de arquivos

- Mantenha arquivos de página (`page.tsx`) simples — eles são o ponto de entrada, não o lugar de lógica complexa
- Lógica fica em hooks, lógica de dados fica em services
- Componentes grandes: quebre em componentes menores

### Performance

- Prefira Server Components para dados iniciais da página
- Use `loading.tsx` para dar feedback visual durante carregamentos
- Use `<Image>` sempre ao invés de `<img>`
- Não importe bibliotecas inteiras quando precisa de uma função só:

```tsx
// ❌ Importa a biblioteca inteira
import _ from 'lodash'
const resultado = _.chunk(array, 3)

// ✅ Importa só o que precisa
import chunk from 'lodash/chunk'
const resultado = chunk(array, 3)
```

### TypeScript

- Nunca use `any`. Se você não sabe o tipo, pesquise ou use `unknown`
- Crie interfaces para os dados que vêm do Supabase
- Use os tipos gerados automaticamente pelo Supabase CLI quando possível

### Segurança

- Sempre valide dados no servidor antes de salvar no banco
- Nunca confie em dados vindos do cliente sem validar (use Zod)
- Variáveis secretas: nunca com `NEXT_PUBLIC_`
- A `SERVICE_ROLE_KEY` do Supabase: apenas em Route Handlers e funções server-side

### Git

- Nunca faça commit do `.env.local`
- Mantenha um `.env.example` com as chaves mas sem os valores
- Use branches para features novas — não desenvolva direto na `main`

---

## 📌 Navegação

[⬅️ Capítulo 16 (Erros Comuns)](./16-erros-comuns.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Glossário Rápido) ➡️](./18-glossario-rapido.md)
