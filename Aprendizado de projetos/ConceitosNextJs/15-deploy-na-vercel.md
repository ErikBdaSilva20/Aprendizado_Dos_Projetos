# Next.js Completo — Capítulo 15

[⬅️ Capítulo 14 (Build e Produção)](./14-build-e-producao.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Erros Comuns) ➡️](./16-erros-comuns.md)

---

## 15. Deploy na Vercel — o jeito mais simples

### Por que Vercel

A Vercel é a empresa que criou o Next.js. O deploy lá é:
- Gratuito para projetos pessoais/pequenos
- Automático: a cada `git push`, um novo deploy acontece
- Zero configuração: ela detecta que é Next.js e sabe o que fazer
- HTTPS automático
- CDN global (seu site fica rápido em qualquer país)

### Como fazer o deploy

1. Crie uma conta em [vercel.com](https://vercel.com)
2. Conecte com seu GitHub
3. Importe o repositório do projeto
4. Configure as variáveis de ambiente (as mesmas do `.env.local`)
5. Clique em Deploy

Pronto. A URL estará no ar em menos de 2 minutos.

### Ambientes na Vercel

A Vercel cria três ambientes automaticamente:

| Ambiente | Quando aparece | URL |
|---|---|---|
| **Production** | Quando você faz push na branch `main` | `seu-projeto.vercel.app` |
| **Preview** | Quando você abre um Pull Request | URL temporária única |
| **Development** | Seu `localhost:3000` local | — |

Cada ambiente pode ter variáveis de ambiente diferentes. Configuração financeira de teste no Preview, configuração real na Production.

### Variáveis de ambiente na Vercel

Na dashboard da Vercel, vá em **Settings → Environment Variables** e adicione as mesmas variáveis do seu `.env.local`. Não se esqueça de adicionar as variáveis de produção do Supabase (que podem ser diferentes das de desenvolvimento).

---

## 📌 Navegação

[⬅️ Capítulo 14 (Build e Produção)](./14-build-e-producao.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Erros Comuns) ➡️](./16-erros-comuns.md)
