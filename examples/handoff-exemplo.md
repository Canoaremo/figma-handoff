# Exemplo de Output — `/handoff`
**Arquivo Figma:** teste-clinica  
**Telas:** Home, Tratamentos, Agendamento  
**Gerado com:** Figma Handoff Skill + Claude AI

> Este é um exemplo real de output gerado a partir de um arquivo Figma de clínica de estética.

---

## TELA 1 — Home (Landing Page)

### Objetivo
Apresentar a proposta editorial da clínica, construir autoridade visual e direcionar o usuário para explorar tratamentos ou iniciar contato.

### Estrutura de Seções

| Seção | Altura | Função |
|---|---|---|
| TopNavBar | 92px | Navegação principal fixa |
| Header — Hero Editorial | 633px | Apresentação da marca |
| Portfolio Bento Grid | 2416px | Grid de casos/tratamentos |
| Asymmetrical Text Interstitial | 357px | Break narrativo editorial |
| Second Grid Layout | 595px | Jornada do paciente |
| CTA Section | 432px | Conversão |
| Footer | 292px | Links e info institucional |

### Componentes de UI

**TopNavBar** — 1280 × 92px
- Logo: texto, alinhado à esquerda, 105×32px
- Menu: 4 links horizontais centralizados, altura 28px
- CTA Button: canto direito, 220×44px, com sombra

**Hero Editorial** — 1280 × 633px
- Heading 1: 677×245px — headline principal
- Body text: 567×98px — subtítulo
- Imagem hero: 474×633px com overlay
- Card flutuante: 319×137px, posicionado sobre a imagem

**Portfolio Bento Grid**
| Card | Dimensões | Conteúdo |
|---|---|---|
| Large Feature | 781×624px | Caso principal com título no rodapé |
| Portrait | 378×948px | Card vertical — Dermatologia |
| Square | 378×624px | Card quadrado — Ingredientes |
| Landscape | 378×300px | Card horizontal sem texto |

### Regras Funcionais
- Hero card flutuante: `position: absolute` dentro do container da imagem
- Bento Grid: CSS Grid com cards de proporções diferentes — usar `aspect-ratio`
- Dois botões CTA distintos — provavelmente primário + secundário

### Critérios de Aceite
- [ ] TopNavBar renderiza fixa no topo com 4 links + botão CTA
- [ ] Hero exibe headline, subtítulo e imagem com card flutuante
- [ ] Bento Grid exibe 4 cards com imagem, categoria e título
- [ ] CTA Section exibe 2 botões centralizados
- [ ] Footer exibe 3 colunas com links e ícones sociais

---

## TELA 3 — Agendamento (Formulário)

### Objetivo
Capturar solicitação de agendamento via formulário simplificado e apresentar informações de contato da clínica.

### Componentes de UI — Formulário

| Campo | Tipo | Label | Placeholder | Obrigatório |
|---|---|---|---|---|
| Nome Completo | Input texto | "Nome Completo" | "Como podemos chamá-lo(a)?" | ✅ |
| Telefone | Input texto | "Telefone / WhatsApp" | "+55 (00) 00000-0000" | ✅ |
| Serviço Desejado | Select/Dropdown | "Serviço Desejado" | — | ✅ |
| Data Preferencial | Date picker | "Data Preferencial" | mm/dd/yyyy | ❌ |

### Regras de Validação

| Campo | Regra | Mensagem de Erro |
|---|---|---|
| Nome | Mín. 3 chars | "Informe seu nome" |
| Telefone | Formato (00) 00000-0000 | "Informe um telefone válido" |
| Serviço | Valor selecionado | "Selecione um serviço" |
| Data | Data futura | "Selecione uma data válida" |

### Critérios de Aceite
- [ ] Formulário exibe 4 campos em layout 2×2
- [ ] Select populado com lista de tratamentos
- [ ] Date picker bloqueia datas passadas
- [ ] Botão habilitado apenas com campos obrigatórios preenchidos
- [ ] Após envio: mensagem de confirmação com prazo de 24h

---

## ⚠️ Pontos de Atenção detectados

| # | Tipo | Elemento | Recomendação |
|---|---|---|---|
| 1 | Estado ausente | Todos os botões | Definir hover, focus, active |
| 2 | Estado ausente | Inputs do formulário | Mapear focus, error, success |
| 3 | Inconsistência | Botão CTA no nav (40px vs 44px) | Padronizar altura across telas |
| 4 | Responsividade | Todas as telas | Nenhuma versão mobile mapeada |
| 5 | Integração | Seção de mapa | Definir Google Maps vs Mapbox |

---

## 🧩 Sugestões de Design System

### Componentes para componentizar
| Componente | Prioridade |
|---|---|
| Button — primário com sombra | 🔴 Alta |
| TopNavBar | 🔴 Alta |
| Footer (3 variações!) | 🔴 Alta |
| TreatmentCard — compacto | 🔴 Alta |
| InputGroup (label + input) | 🟡 Média |

### Tokens sugeridos
```css
--spacing-page-margin: 48px;
--spacing-section-gap: 128px;
--button-height-md: 48px;
--button-height-lg: 54px;
--card-padding: 32px;
```

---

*Output gerado automaticamente pela [Figma Handoff Skill](https://github.com/seu-usuario/figma-handoff-skill)*
