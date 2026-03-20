# Give&Grow + PatasDF

> Comunidade gratuita de troca, aprendizado e voluntariado no Distrito Federal — com o PatasDF como uma das causas dentro do ecossistema.

---

## Sobre o projeto

O **Give&Grow** é uma plataforma comunitária e 100% gratuita que conecta pessoas do Distrito Federal que querem **aprender**, **ensinar** e **fazer voluntariado**. Sem burocracia, sem cadastro obrigatório, sem custo.

O **PatasDF** nasceu dentro desse ecossistema como uma causa dedicada à proteção animal: ajuda a reencontrar animais perdidos no DF, lista animais encontrados aguardando o dono e reúne ONGs da causa animal.

Ambos os projetos foram criados por **Clarice Nunes**, estudante de Engenharia de Software no CEUB, como uma forma de usar tecnologia para gerar impacto social real na comunidade do DF.

---

## Estrutura de arquivos

```
give-grow/
│
├── index.html          # Página principal do Give&Grow
├── patasdf.html        # Página principal do PatasDF
├── animais.html        # Listagem de animais disponíveis para adoção
├── causas.html         # Todas as áreas de interesse da comunidade
├── sobre.html          # Sobre a criadora (Clarice Nunes)
├── voluntariado.html   # Página de interesse em voluntariado
├── styles.css          # Folha de estilos unificada
├── animais.json        # Base de dados dos animais (perdidos/encontrados/adoção)
│
└── fotos/
    ├── clarice2.jpg    # Foto da criadora (perfil)
    ├── bolt.jpg        # Foto do Bolt (in memoriam)
    └── max.jpg         # Foto da Max (in memoriam)
```

---

## Como rodar localmente

O projeto é 100% estático — sem back-end, sem dependências externas, sem build.

**1. Clone o repositório:**
```bash
git clone https://github.com/claricenunes/give-grow.git
cd give-grow
```

**2. Abra no navegador:**

Você pode simplesmente abrir o `index.html` diretamente no navegador, ou usar uma extensão como o **Live Server** no VS Code para ter hot reload.

```bash
# Com Live Server (VS Code) — instale a extensão e clique em "Go Live"
# Ou com Python:
python3 -m http.server 3000
# Acesse: http://localhost:3000
```

---

## Configuração dos formulários

Os formulários de participação usam **Google Forms**. Para configurar, substitua os placeholders abaixo nos arquivos HTML:

| Placeholder | Arquivo | Descrição |
|---|---|---|
| `SEU_LINK_GOOGLE_FORMS_APRENDER` | `index.html` | Formulário de quem quer aprender |
| `SEU_LINK_GOOGLE_FORMS_ENSINAR` | `index.html` | Formulário de quem quer ensinar |
| `SEU_LINK_GOOGLE_FORMS_VOLUNTARIADO` | `voluntariado.html` | Formulário de interesse em voluntariado |
| `SEU_LINK_GOOGLE_FORMS_PERDI` | `patasdf.html` | Formulário de animal perdido |
| `SEU_LINK_GOOGLE_FORMS_ENCONTREI` | `patasdf.html` | Formulário de animal encontrado |

---

## Configuração do PatasDF (`animais.json`)

Os animais exibidos na plataforma são carregados a partir do arquivo `animais.json`. Se o arquivo não for encontrado, o sistema exibe automaticamente os dados de exemplo embutidos no código.

### Estrutura do `animais.json`

```json
[
  {
    "id": "001",
    "nome": "Bolinha",
    "status": "perdido",
    "tipo": "cachorro",
    "idade": "~2 anos",
    "porte": "Médio",
    "cidade": "Asa Sul",
    "descricao": "Vira-lata caramelo com mancha branca no peito.",
    "contato": "(61) 98888-1111"
  },
  {
    "id": "002",
    "nome": "Mimi",
    "status": "encontrado",
    "tipo": "gato",
    "idade": "~1 ano",
    "porte": "Pequeno",
    "cidade": "Taguatinga",
    "descricao": "Gatinha listrada, muito dócil. Aguardando dono.",
    "contato": "(61) 97777-2222"
  }
]
```

**Valores válidos para `status`:** `perdido` · `encontrado` · `disponivel` (para adoção)

**Valores válidos para `tipo`:** `cachorro` · `gato`

>  **Dica:** Você pode automatizar a atualização do `animais.json` conectando o Google Forms ao Google Sheets e usando Google Apps Script para exportar os dados como JSON a cada nova resposta.

---

## Configuração do Google Calendar

A seção de eventos usa o **Google Calendar** incorporado via iframe. Para configurar:

1. Acesse seu Google Calendar
2. Nas configurações do calendário, vá em **Integrar calendário**
3. Copie o link de incorporação (`iframe`)
4. Substitua a URL no `index.html` na seção `calendarEmbed`

---

## Tecnologias utilizadas

| Tecnologia | Uso |
|---|---|
| HTML5 + CSS3 | Estrutura e estilo de todas as páginas |
| JavaScript (vanilla) | Interatividade, modais, filtros, IntersectionObserver |
| Google Fonts | Playfair Display + DM Sans |
| Google Forms | Coleta de dados dos participantes |
| Google Sheets | Armazenamento das respostas dos formulários |
| Google Apps Script | Automação e exportação dos dados |
| Google Calendar | Agenda de eventos incorporada |
| Google My Maps | Mapa de animais perdidos/encontrados |
| GitHub Pages | Hospedagem estática gratuita |

---

## Páginas do projeto

### Give&Grow

| Página | Descrição |
|---|---|
| `index.html` | Hero, causas, eventos, seção de participação, PatasDF e sobre |
| `causas.html` | Todas as 20+ áreas de interesse com filtros por categoria |
| `voluntariado.html` | Página de interesse em voluntariado com formulário e seção para ONGs |
| `sobre.html` | Perfil da criadora, história do projeto e tecnologias |

### PatasDF

| Página | Descrição |
|---|---|
| `patasdf.html` | Hero, formulários de perdi/encontrei, listagem de animais, mapa e ONGs |
| `animais.html` | Listagem completa de animais disponíveis para adoção com busca e filtros |

---

## Funcionalidades

- **Modais de redirecionamento** — Antes de ir para o Google Forms, o usuário vê uma explicação do que será coletado e para quê
- **Termo de veracidade** (PatasDF) — Ao cadastrar animal perdido ou encontrado, o usuário aceita um termo com checkbox obrigatório antes de acessar o formulário
- **Filtros dinâmicos** — Nas páginas de causas e animais, filtros por categoria com scroll automático
- **Reveal on scroll** — Elementos aparecem suavemente conforme o usuário rola a página (IntersectionObserver)
- **Ticker animado** — Faixa com eventos e destaques da comunidade em loop
- **Cards flutuantes** — Hero com cards de exemplo animados (float CSS)
- **Navbar responsiva** — Menu hamburguer no mobile, navbar com efeito de scroll
- **Google Calendar integrado** — Agenda completa colapsável com iframe
- **Design responsivo** — Funciona em mobile, tablet e desktop

---

## Design

- **Tipografia:** Playfair Display (títulos, display) + DM Sans (corpo, UI)
- **Paleta:**
  - `#0e1a0f` — Ink (fundo escuro, textos)
  - `#4a7c59` — Sage (cor principal)
  - `#c4922a` — Gold (destaque, PatasDF encontrado)
  - `#f5f0e8` — Cream (fundo claro)
  - `#b85c38` — Rust (alertas, perdido)
- **Animações:** CSS puro — fadeUp, orbFloat, cardFloat, dotPulse, ticker
- **Layout:** CSS Grid + Flexbox, responsivo sem frameworks

---

## Deploy no GitHub Pages

1. Faça o push de todos os arquivos para a branch `main`
2. Acesse **Settings → Pages** no repositório
3. Em **Source**, selecione `Deploy from a branch` → `main` → `/ (root)`
4. Aguarde alguns minutos e acesse `https://seu-usuario.github.io/give-grow`

>  Certifique-se de que todas as referências a arquivos usam caminhos relativos (ex: `fotos/clarice2.jpg` e não `/fotos/clarice2.jpg`) para funcionar corretamente no GitHub Pages.

---

## Próximos passos

- [ ] Integração com Google Sheets via Apps Script para atualizar `animais.json` automaticamente
- [ ] Página de perfil de cada animal com mais fotos
- [ ] Sistema de notificação por email quando alguém cadastra um animal na mesma região
- [ ] Mapa interativo com Google My Maps integrado
- [ ] Expansão do voluntariado com parcerias com ONGs do DF
- [ ] Página de eventos com inscrição direta

---

## Criadora

**Clarice Nunes**
Estudante de Engenharia de Software · Brasília, DF

[![Instagram](https://img.shields.io/badge/Instagram-%40claricesnunes-E1306C?style=flat&logo=instagram&logoColor=white)](https://instagram.com/claricesnunes)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-claricesnunes-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/claricesnunes)
[![GitHub](https://img.shields.io/badge/GitHub-claricenunes-333?style=flat&logo=github&logoColor=white)](https://github.com/claricenunes)
[![Email](https://img.shields.io/badge/Email-euclaricenunes%40gmail.com-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:euclaricenunes@gmail.com)

> *"Queria usar a tecnologia para gerar impacto social de verdade. Vejo gente querendo ajudar, mas sem saber como. Vejo gente querendo aprender, mas sem acesso. Então decidi criar um lugar que conecta essas duas partes."*

---

##  Licença

Este projeto é de uso pessoal e educacional.

---

<div align="center">
  Feito com 🌱 e 🐾 por <a href="https://github.com/claricenunes">Clarice Nunes</a> · Brasília, DF · 2025
</div>
