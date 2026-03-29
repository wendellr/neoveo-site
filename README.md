# Neoveo.ai — Landing Page

Landing page institucional da **Neoveo.ai**, startup B2B de visão computacional aplicada para indústria, agricultura, energia, logística, segurança do trabalho e varejo.

> **Stack:** HTML estático + CSS + JS vanilla — sem build system, sem framework.

---

## Estrutura do projeto

```
neoveo-web/
├── index.html                          # Página principal (HTML + CSS inline + i18n inline)
├── assets/
│   ├── brand/
│   │   ├── icons/
│   │   │   ├── neoveo_favicon.ico
│   │   │   ├── neoveo_icon_128.png
│   │   │   └── neoveo_icon_nobg_128.png
│   │   └── logos/
│   │       └── neoveo_logo_nobg_512.png
│   ├── css/
│   │   └── site.css                    # Estilos extraídos (reserva para refatoração)
│   └── js/
│       └── site.js                     # JS extraído com sistema i18n (reserva para refatoração)
└── .gitignore
```

> **Nota:** O `index.html` atual é self-contained — CSS e JS estão inline no próprio arquivo. Os arquivos `site.css` e `site.js` em `assets/` são versões extraídas preparadas para uma futura migração (ex.: Next.js).

---

## Seções da página

| Seção | ID/âncora | Descrição |
|---|---|---|
| Navbar | — | Logo, links de navegação, seletor de idioma, CTA |
| Hero | `#top` | Headline, badge, CTAs, mockup com imagem de drone |
| Trust bar | — | Marquee com parceiros/referências (Equatorial, Postalis, ANEEL, etc.) |
| Stats | — | Métricas: 25+ demos, 6 verticais, 15+ anos, PhD |
| Verticals | `#verticals` | 6 cards: Agriculture, Manufacturing, Logistics, Energy, Workplace Safety, Retail |
| Demos | `#demos` | 3 demos em destaque: PPE Detection, Solar Thermography, Crop Disease |
| Photo banner | — | Banner full-bleed "from cloud to edge" |
| Services | `#services` | Grid de 12 serviços (annotation, training, edge deploy, SCADA, etc.) |
| CTA / Contact | `#contact` | Formulário de lead (protótipo — abre draft de e-mail) |
| Footer | — | Links, logo dark variant, legal (LGPD/GDPR/CCPA) |

---

## Internacionalização (i18n)

O sistema de tradução é client-side puro, embutido no `<script>` ao final do `index.html`.

**Idiomas suportados:** EN · PT · FR · ES

**Como funciona:**
- Elementos com `data-i18n="chave"` → `textContent` substituído
- Elementos com `data-i18n-html="chave"` → `innerHTML` substituído (para tags como `<em>`)
- Elementos com `data-i18n-ph="chave"` → `placeholder` substituído
- O idioma é salvo em `localStorage` com a chave `neoveo-lang`

**Para adicionar uma tradução:**
1. Localize o objeto `T` no `<script>` final do `index.html`
2. Adicione a chave em todos os 4 blocos de idioma (`en`, `pt`, `fr`, `es`)
3. Use o atributo `data-i18n` no elemento HTML correspondente

---

## Desenvolvimento local

Não há build step. Basta servir os arquivos estáticos:

```bash
# Opção 1 — Python
python3 -m http.server 8000

# Opção 2 — Node
npx serve .

# Opção 3 — VS Code
# Instale a extensão "Live Server" e clique em "Go Live"
```

Abra `http://localhost:8000` no navegador.

---

## Assets visuais

**Imagens externas (Unsplash):** Todas as imagens de seção (hero, verticals, demos, banner) são carregadas via CDN do Unsplash. Para produção, substituir por imagens locais em `assets/img/`.

**Brand assets locais:**
| Arquivo | Uso |
|---|---|
| `neoveo_favicon.ico` | Favicon do site |
| `neoveo_icon_128.png` | Ícone no footer (fundo escuro) |
| `neoveo_icon_nobg_128.png` | Ícone no header (fundo claro) |
| `neoveo_logo_nobg_512.png` | Logo alta resolução (marketing) |

---

## Convenções

- **Commits:** formato [Conventional Commits](https://www.conventionalcommits.org/) — `feat:`, `fix:`, `docs:`, `style:`, `refactor:`
- **Branch principal:** `main`
- **CSS:** variáveis definidas em `:root` no `<style>` do `index.html` (palettes, fonts, radii)
- **Fontes:** Cabinet Grotesk (headings), General Sans (body), IBM Plex Mono (labels/badges)
- **Cores principais:** `--accent: #1a8cff` (azul), `--dark: #0d1117` (seções escuras)

---

## Próximos passos

- [ ] Substituir imagens Unsplash por assets locais
- [ ] Integrar formulário com CRM (HubSpot webhook)
- [ ] Criar sub-páginas por vertical
- [ ] Migração para Next.js com static export
- [ ] Deploy via GitHub Pages ou Vercel

---

## Licença

Proprietário — **Neoveo.ai / Trustd Solutions**. Todos os direitos reservados.
