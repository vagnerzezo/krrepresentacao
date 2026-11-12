# KR Representações

Site institucional da **KR Representações**, empresa de gestão de marcas de moda que atua no Rio Grande do Sul desde 2019, com showroom em São Leopoldo/RS.

O site apresenta a empresa, as marcas representadas (QIX, West Coast, Orange, Tropical Brasil), produtos, o showroom e depoimentos de parceiros. O pedido de catálogo é feito pelo WhatsApp.

## Tecnologias

- [Nuxt 3](https://nuxt.com/) (Vue 3 + Vue Router)
- [Tailwind CSS 4](https://tailwindcss.com/) via `@tailwindcss/vite`
- TypeScript

## Requisitos

- Node.js 18 ou superior (recomendado: 20+)
- npm

## Como rodar

```bash
# instalar dependências
npm install

# servidor de desenvolvimento em http://localhost:3000
npm run dev
```

## Scripts

| Comando            | Descrição                                          |
| ------------------ | -------------------------------------------------- |
| `npm run dev`      | Inicia o servidor de desenvolvimento               |
| `npm run build`    | Gera o build de produção (SSR) em `.output/`       |
| `npm run generate` | Gera o site estático (pré-renderizado)             |
| `npm run preview`  | Serve localmente o build de produção               |

## Estrutura

```
├── app.vue              # Layout raiz: Navbar fixa, página atual e Rodapé
├── assets/css/main.css  # CSS global (Tailwind)
├── components/
│   ├── About/           # Seção "Sobre nós"
│   ├── Brand/           # Marcas representadas + botão de catálogo
│   ├── Depoimento/      # Depoimentos de parceiros
│   ├── Fullbanner/      # Banner principal da home
│   ├── Navbar/          # Menu de navegação (com menu hambúrguer no mobile)
│   ├── Product/         # Vitrine de produtos
│   ├── Rodape/          # Rodapé com contato e endereço
│   └── Showroom/        # Galeria do showroom
├── pages/               # Rotas (geradas automaticamente pelo Nuxt)
│   ├── index.vue        # /             → Fullbanner + Sobre nós
│   ├── marcas.vue       # /marcas
│   ├── produtos.vue     # /produtos
│   ├── showroom.vue     # /showroom
│   └── depoimentos.vue  # /depoimentos
├── public/img/          # Imagens, logos das marcas e fotos do showroom
└── nuxt.config.ts       # Configuração do Nuxt e do Tailwind
```

Os componentes em `components/` são importados automaticamente pelo Nuxt; basta usar `<Brand />`, `<Rodape />` etc. nas páginas.

## Deploy

`npm run generate` gera um site estático em `.output/public`, que pode ser publicado em qualquer hospedagem estática (Netlify, Vercel, GitHub Pages, S3 etc.). Para rodar com SSR, use `npm run build` e inicie com `node .output/server/index.mjs`.

Mais detalhes na [documentação de deploy do Nuxt](https://nuxt.com/docs/getting-started/deployment).

## Contato

- **Telefone:** (51) 98148-1121
- **E-mail:** comercial@krrepresentacao.com.br
- **Endereço:** Rua Medianeira, 322 - Cristo Rei - São Leopoldo/RS - CEP 93020-440
