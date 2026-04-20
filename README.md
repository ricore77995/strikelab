# Strikelab Cascais

Static site — one `index.html` + assets. Zero build.

## Deploy no Vercel

### Opção A — Via GitHub (recomendada)
1. Faz push destes ficheiros para `https://github.com/ricore77995/strikelab` (branch `main`).
2. Abre [vercel.com/new](https://vercel.com/new), escolhe o repo `strikelab`.
3. **Framework Preset:** `Other` · **Build Command:** (vazio) · **Output Directory:** `./`
4. Clica **Deploy**. Fica online em `strikelab-xxxx.vercel.app`.

### Opção B — Via Vercel CLI (sem GitHub)
```bash
npm i -g vercel
cd deploy
vercel
```

## Domínio próprio
Em Vercel → Project → Settings → Domains → adiciona `strikelab.pt` (ou o que quiseres) e aponta o DNS do registrar para os nameservers do Vercel.

## Estrutura
```
deploy/
├── index.html           # site completo
├── assets/
│   ├── hero-bg.mp4
│   ├── hero-bg-2.mp4
│   ├── studio-topdown.jpg
│   ├── studio-topdown-2.jpg
│   └── locker-room.jpg
├── vercel.json          # cache headers para assets
├── .gitignore
└── README.md
```

## Editar conteúdo
Todo o site vive num único `index.html`. Copy bilingue (PT/EN) está no objeto `I18N` no final do ficheiro.
