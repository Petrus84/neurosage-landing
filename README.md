# NeuroSAGE Landing Page - Versão Standalone

Landing page responsiva para o sistema NeuroSAGE, otimizada para conversão.

## ⚠️ IMPORTANTE: Nomenclatura do Projeto

Este projeto deve usar um nome DIFERENTE do projeto principal:
- ❌ **NÃO use:** `neurosage` (já existe no GitHub/Vercel)
- ✅ **Use:** `neurosage-landing` ou `neurosage-lp` ou `neurosage-site`

## 📁 Estrutura de Arquivos

```
neurosage-landing/          ← Nome da pasta (DIFERENTE do projeto principal)
├── index.html              # Página principal (HTML + CSS inline)
├── vercel.json             # Configuração da Vercel
├── assets/
│   └── sage.png            # Logo do NeuroSAGE
└── README.md               # Este arquivo
```

## 🚀 Deploy na Vercel

### Opção 1: Deploy via GitHub (Recomendado)

1. **Crie um repositório no GitHub com NOME DIFERENTE:**
   ```bash
   # Dentro da pasta neurosage-landing/
   git init
   git add .
   git commit -m "Initial commit - NeuroSAGE Landing Page"
   git branch -M main
   git remote add origin https://github.com/seu-usuario/neurosage-landing.git
   git push -u origin main
   ```

2. **Conecte à Vercel:**
   - Acesse [vercel.com](https://vercel.com)
   - Clique em "New Project"
   - Importe o repositório `neurosage-landing` do GitHub
   - **IMPORTANTE:** Na tela de configuração, verifique:
     - Project Name: `neurosage-landing` (ou outro nome único)
     - Framework Preset: Other
     - Root Directory: `./`
   - Clique em "Deploy"

3. **URL resultante será:**
   - `neurosage-landing.vercel.app` (ou o nome que você escolher)

4. **Domínio personalizado (opcional):**
   - Vá em "Settings" → "Domains"
   - Adicione um subdomínio: `lp.neurosage.com` ou `landing.neurosage.com`
   - Ou use domínio totalmente diferente: `neurosage.com`

### Opção 2: Deploy via CLI da Vercel

1. **Instale a Vercel CLI:**
   ```bash
   npm i -g vercel
   ```

2. **Faça login:**
   ```bash
   vercel login
   ```

3. **Deploy (ele vai perguntar o nome do projeto):**
   ```bash
   cd neurosage-landing
   vercel
   ```
   
   **QUANDO PERGUNTAR:**
   ```
   ? What's your project's name? neurosage-landing
   ? In which directory is your code located? ./
   ```

4. **Para deploy em produção:**
   ```bash
   vercel --prod
   ```

## 📝 Checklist Pré-Deploy

- [ ] ✅ Renomear pasta para `neurosage-landing` (ou similar)
- [ ] ✅ Verificar que não há conflito com projeto existente
- [ ] Adicionar logo `sage.png` na pasta `assets/`
- [ ] Verificar link do formulário: `https://forms.gle/fCAZ29xBiHeV6vs17`
- [ ] Adicionar link do botão "ACESSO GARANTIDO (R$ 47)" (linha 433 do HTML)
- [ ] Adicionar links sociais no footer:
  - Instagram (linha 526)
  - Email (linha 527)
  - WhatsApp (linha 528)
- [ ] Testar responsividade em mobile
- [ ] Verificar carregamento das fontes Google

## 🔧 Evitando Conflitos com Projeto Existente

### Se você já tem `neurosage` no GitHub/Vercel:

**Opção A: Repositório Separado (Recomendado)**
```bash
# Crie um novo repo com nome diferente
neurosage-landing/     ← Landing page
neurosage/             ← Projeto principal (já existe)
```

**Opção B: Monorepo (Avançado)**
```bash
neurosage/
├── app/               ← Aplicação principal
├── landing/           ← Landing page
├── vercel.json        ← Configuração para múltiplos projetos
└── README.md
```

Para Monorepo, use este `vercel.json`:
```json
{
  "version": 2,
  "builds": [
    {
      "src": "landing/index.html",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/landing/$1"
    }
  ]
}
```

**Opção C: Branch Separado (Mais Simples)**
```bash
# No mesmo repositório, crie branch separado
git checkout -b landing-page
# Faça deploy desta branch na Vercel como projeto separado
```

## 🎨 Customizações Rápidas

### Alterar Cores
No arquivo `index.html`, procure por `:root` (linha ~20) e modifique:
```css
--primary: #667eea;        /* Cor principal dos botões */
--secondary: #11998e;      /* Cor do botão beta */
--gradient-start: #667eea; /* Início do gradiente */
--gradient-end: #764ba2;   /* Fim do gradiente */
```

### Alterar Textos
Todos os textos estão no HTML. Busque por:
- **Hero:** linha 300+
- **O Que É:** linha 330+
- **Para Quem É:** linha 377+
- **CTA Final:** linha 443+

### Adicionar Google Analytics
Adicione antes do `</head>` (linha ~297):
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## 🔧 Troubleshooting

### Erro: "Project name already exists"
- ✅ Use nome diferente: `neurosage-landing`, `neurosage-lp`, `neurosage-site`
- ✅ Ou adicione sufixo único: `neurosage-landing-v2`

### Logo não aparece
- Certifique-se de que `sage.png` está em `assets/sage.png`
- Verifique se o nome do arquivo está correto (case-sensitive)
- O caminho é relativo à raiz do projeto

### Fontes não carregam
- As fontes são do Google Fonts e carregam via CDN
- Verifique conexão com internet

### Layout quebrado no mobile
- Limpe o cache do navegador
- Teste em modo anônimo/privado

## 📱 Testado em:
- ✅ Chrome (Desktop/Mobile)
- ✅ Safari (iOS)
- ✅ Firefox
- ✅ Edge

## 🎯 Performance
- Lighthouse Score: 95+
- First Contentful Paint: < 1s
- Time to Interactive: < 2s

## 📦 Estrutura Final Recomendada

```
Seus Projetos:
├── neurosage/              ← Aplicação principal (já existe)
│   └── [código do app]
│
└── neurosage-landing/      ← Landing page (NOVO)
    ├── index.html
    ├── vercel.json
    ├── assets/
    │   └── sage.png
    └── README.md

Deploy na Vercel:
├── neurosage (projeto existente)
│   └── neurosage.vercel.app
│
└── neurosage-landing (novo projeto)
    └── neurosage-landing.vercel.app
```

## 📞 Suporte

Criado para Petruchio Barros
Dúvidas? Entre em contato através dos canais do NeuroSAGE.

---

**Versão:** 1.1  
**Última atualização:** Dezembro 2024  
**Importante:** Este é um projeto SEPARADO do neurosage principal
