# Sistema Book Fair

Front-end do sistema: login, menus e todas as telas.
É um arquivo só (`index.html`), sem build e sem instalação.

## Estrutura

```
Sistema Book Fair
├── Portal E-Commerce
│   ├── Relatórios
│   │   ├── Relatório dos Comunicados      (Supabase)
│   │   ├── Relatório atual das lojas      (backend no Render)
│   │   └── List Status Colégios           (em desenvolvimento)
│   ├── Comunicados
│   │   ├── Consultar / Gerar por código
│   │   └── Consultar Modelos
│   └── APIs Configuração de E-Commerce    (em desenvolvimento)
├── List Microsoft                          (em desenvolvimento)
└── Status Correio                          (em desenvolvimento)
```

## Com o que ele conversa

| Serviço | Onde | Para quê |
|---|---|---|
| Supabase | `irbpjkgqkquovmrzpvfv.supabase.co` | Login, usuários, colégios, comunicados |
| Backend | `portal-ecommerce-backend.onrender.com` | Relatório atual das lojas (dados da Layers) |

Ambos já estão configurados no topo do arquivo:

```js
const SUPABASE_URL  = "https://irbpjkgqkquovmrzpvfv.supabase.co";
const BACKEND_URL   = "https://portal-ecommerce-backend.onrender.com";
```

## Sobre a chave do Supabase no código

A chave `anon` fica visível no arquivo — é assim mesmo que ela foi projetada,
porque roda no navegador de quem acessa. Quem protege os dados é o RLS
(Row Level Security), ativo em todas as tabelas: sem login válido, o banco
não devolve nada, e cada perfil só enxerga o que lhe cabe.

Nenhum token da Layers aparece aqui. Eles ficam só no backend, em variáveis
de ambiente no Render.

## Publicar

Qualquer hospedagem de site estático serve. Na Vercel:

1. Conecte a conta do GitHub
2. **Add New → Project** e escolha este repositório
3. Framework: **Other**. Build e Output: deixe em branco
4. **Deploy**

Cada `push` na branch `main` republica sozinho. Cada branch ganha um link
de teste próprio, para experimentar antes de valer para todos.

## Testar na sua máquina

Basta abrir o `index.html` no navegador. Não precisa de servidor.

## Depois de publicar

Ajuste o `ORIGENS_PERMITIDAS` do backend no Render, trocando `*` pelo
endereço publicado. É o que impede outros sites de usarem o seu backend.
