# Next.js Completo — Capítulo 11

[⬅️ Capítulo 10 (Variáveis de Ambiente)](./10-variaveis-de-ambiente.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Metadata e SEO) ➡️](./12-metadata-e-seo.md)

---

## 11. Imagens, Fontes e Assets

### O componente `<Image>` do Next.js

**Nunca use `<img>` diretamente no Next.js.** Use o componente `<Image>` do pacote `next/image`. Ele automaticamente:
- Otimiza o tamanho da imagem
- Converte para formatos modernos (WebP, AVIF)
- Carrega com lazy loading
- Evita layout shift (aquele "pulo" quando a imagem carrega)

```tsx
import Image from 'next/image'

// Imagem local (da pasta public/)
<Image
  src="/logo.png"
  alt="Logo da academia"
  width={200}
  height={80}
/>

// Imagem de URL externa (Supabase Storage, por exemplo)
<Image
  src={aluno.avatar_url}
  alt={aluno.nome}
  width={48}
  height={48}
  className="rounded-full"
/>
```

Para imagens externas, você precisa configurar os domínios permitidos em `next.config.ts`:

```ts
// next.config.ts
const nextConfig = {
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: '*.supabase.co', // permite imagens do Supabase Storage
      }
    ]
  }
}
```

### Fontes com `next/font`

O Next.js tem um sistema de fontes embutido que baixa a fonte uma vez e serve do próprio servidor, evitando requisições externas ao Google Fonts (mais rápido e mais privado).

```tsx
// app/layout.tsx
import { Inter, Roboto_Mono } from 'next/font/google'

const inter = Inter({
  subsets: ['latin'],
  variable: '--font-inter', // cria uma variável CSS
})

export default function RootLayout({ children }) {
  return (
    <html className={inter.variable}>
      <body>{children}</body>
    </html>
  )
}
```

### Arquivos estáticos (pasta `public/`)

Tudo que você colocar na pasta `public/` fica acessível pela URL diretamente:

```
public/
  logo.png        → acessível em /logo.png
  favicon.ico     → acessível em /favicon.ico
  icons/
    apple.png     → acessível em /icons/apple.png
```

---

## 📌 Navegação

[⬅️ Capítulo 10 (Variáveis de Ambiente)](./10-variaveis-de-ambiente.md) | [Índice](./GUIA_NEXTJS_COMPLETO.md) | [Próximo Capítulo (Metadata e SEO) ➡️](./12-metadata-e-seo.md)
