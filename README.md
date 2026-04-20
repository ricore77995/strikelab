# Strikelab Cascais

Site estático — um único `index.html` + 5 assets (2 vídeos, 3 imagens). Zero build.

## Deploy no Vercel — CLI direto (RECOMENDADO)

Este método salta o GitHub completamente. 30 segundos, zero drama:

```bash
npm i -g vercel
cd deploy
vercel          # segue o prompt (login Vercel, "Link to existing project? No", nome, etc.)
vercel --prod   # promove para produção
```

Fica online em `strikelab-xxxx.vercel.app`. Depois em Vercel → Settings → Domains adicionas `strikelab.pt` e apontas DNS.

## Deploy via GitHub

1. **Push para o repo** (confirma que os MP4s vão — ver abaixo):
   ```bash
   cd deploy
   git init
   git add .
   git status                   # DEVE listar assets/*.mp4
   git commit -m "Strikelab site"
   git branch -M main
   git remote add origin https://github.com/ricore77995/strikelab.git
   git push -u origin main --force
   ```

2. **Vercel** → [vercel.com/new](https://vercel.com/new) → escolhe `ricore77995/strikelab`:
   - Framework Preset: `Other`
   - Build Command: **vazio**
   - Output Directory: **vazio** (usa a root)
   - Clica **Deploy**

## Se os vídeos não carregarem no Vercel

Causa mais comum: **os MP4s não foram commitados**.

Verifica:
```bash
# No repo clonado, deve listar os 2 ficheiros:
git ls-files assets/ | grep mp4
```

Se estiver vazio, força:
```bash
git add -f assets/hero-bg.mp4 assets/hero-bg-2.mp4
git commit -m "add videos"
git push
```

Também confirma no GitHub web: `ricore77995/strikelab/tree/main/assets` deve mostrar os `.mp4` com tamanho ~6MB.

## Estrutura
```
deploy/
├── index.html
├── assets/
│   ├── hero-bg.mp4            (6.0 MB)
│   ├── hero-bg-2.mp4          (6.2 MB)
│   ├── studio-topdown.jpg
│   ├── studio-topdown-2.jpg
│   └── locker-room.jpg
├── vercel.json                # Content-Type + Accept-Ranges para vídeos
├── .gitignore
└── README.md
```

## Editar conteúdo
Todo o site vive em `index.html`. Copy bilingue (PT/EN) está no objeto `I18N` no final do ficheiro. Idioma default: EN.
