---
name: figma-handoff
description: >
  Especialista em transformar telas conectadas do Figma em documentação completa de handoff para desenvolvimento.
  Use esta skill SEMPRE que um arquivo Figma estiver conectado via MCP e o objetivo for gerar documentação técnica,
  specs de componentes, fluxos de navegação, auditorias de UX ou PRDs curtos para times de engenharia e produto.
  Ative quando o usuário mencionar: handoff, figma handoff, specs para dev, documentação de telas, fluxo de navegação,
  auditoria de componentes, gaps de UX, dev-ready, PRD curto, ou quando usar os comandos /handoff, /flow-map,
  /component-audit, /ux-gaps, /dev-ready ou /prd-short.
  Esta skill requer o MCP do Figma conectado para leitura dos frames, componentes e protótipos.
compatibility: "Requer Figma MCP conectado"
---

# Figma Handoff Skill

Transforma telas do Figma em documentação técnica completa e pronta para engenharia, produto e QA.
**Nunca apenas descreva visuais. Sempre traduza design em lógica de implementação.**

---

## Comandos Disponíveis

| Comando | Ação |
|---|---|
| `/handoff` | Handoff técnico completo das telas selecionadas |
| `/flow-map` | Mapeia navegação e fluxo de usuário entre telas |
| `/component-audit` | Lista componentes reutilizáveis e oportunidades de design system |
| `/ux-gaps` | Detecta estados ausentes, inconsistências e interações ambíguas |
| `/dev-ready` | Especificação pronta para desenvolvimento |
| `/prd-short` | PRD curto para Jira / Linear |

---

## Fluxo de Execução

### Passo 1 — Analisar estrutura
Use as ferramentas do Figma MCP (`get_design_context`, `get_metadata`, `get_screenshot`) para identificar:
- Hierarquia de telas e seções
- Composição de layout, grids e espaçamentos
- Tipografia e tokens de cor

### Passo 2 — Detectar componentes
Mapeie via MCP (`search_design_system`, `get_variable_defs`):
- Botões, inputs, cards, modais, tabelas, blocos de navegação
- Variantes e padrões repetidos
- Inconsistências de nomenclatura

### Passo 3 — Inferir comportamento
A partir dos protótipos e estados visíveis, detecte:
- Elementos clicáveis e transições
- Estados: hover, loading, disabled, error, success

### Passo 4 — Inferir lógica de negócio
Traduza a UI em:
- Ações do usuário e validações
- Pontos de decisão e edge cases

### Passo 5 — Gerar output
Use o template abaixo conforme o comando solicitado.

---

## Template de Output — `/handoff` e `/dev-ready`

```
# [Nome da Feature]

## Objetivo
O que esta tela resolve para o usuário.

## Fluxo Principal do Usuário
Passo a passo da interação.

## Componentes de UI
Lista detalhada dos elementos de interface com specs.

## Regras Funcionais
Lógica de comportamento.

## Regras de Validação
Validações obrigatórias.

## Estados
- Default
- Hover
- Active
- Disabled
- Loading
- Error
- Success

## Responsividade
Comportamento em desktop / tablet / mobile.

## Notas Técnicas
Dependências e considerações de implementação.

## Critérios de Aceite
Checklist claro de entrega.
```

---

## Template de Output — `/prd-short`

```
## Problema
O que este problema resolve.

## Solução
Resumo da feature.

## Valor para o Usuário
Impacto esperado.

## Escopo de Entrega
Limites de implementação.
```

---

## Template de Output — `/flow-map`

Liste cada tela como nó e mapeie as conexões de protótipo:
```
[Tela A] --ação--> [Tela B]
[Tela A] --erro--> [Tela C: Error State]
```
Se não houver links de protótipo, infira o fluxo pela lógica visual e nomeie como "fluxo inferido".

---

## Template de Output — `/component-audit`

```
## Componentes Identificados
| Componente | Variantes | Reutilizável | Observação |
|---|---|---|---|

## Oportunidades de Design System
- Sugestões de tokenização
- Padrões para consolidar
- Normalização de nomenclatura sugerida
```

---

## Template de Output — `/ux-gaps`

```
## Gaps de UX Detectados
| Item | Tipo | Tela | Recomendação |
|---|---|---|---|

Tipos: estado ausente | espaçamento inconsistente | label ambíguo | componente duplicado | ação ambígua
```

---

## Camada de Auditoria UX (sempre executar)

Independente do comando, sempre verifique:
- Estados ausentes (loading, erro, vazio, sucesso)
- Espaçamentos inconsistentes
- Labels inconsistentes ou ambíguos
- Componentes duplicados que poderiam ser unificados
- Ações sem feedback visual claro

Reporte ao final do output principal como seção **"⚠️ Pontos de Atenção"**.

---

## Sugestões de Design System (sempre incluir)

Ao final de qualquer output, adicione seção **"🧩 Sugestões de Design System"** com:
- Componentes candidatos a reutilização
- Tokens que poderiam ser padronizados
- Padrões visuais recorrentes que merecem consolidação

---

## Comportamento Avançado

**Se existirem links de protótipo:** infira a lógica de navegação automaticamente via conexões MCP.

**Se os nomes de componentes forem inconsistentes:** sugira normalização de nomenclatura ao final.

**Se as telas estiverem incompletas:** liste perguntas abertas para o time de produto na seção **"❓ Perguntas em Aberto"**.

**Se não houver MCP do Figma conectado:** informe o usuário que esta skill requer a integração Figma MCP ativa e oriente a conectá-la nas configurações de ferramentas.

---

## Estilo de Escrita

- Conciso e técnico
- Orientado a produto
- Amigável para engenharia
- Sem jargão de design desnecessário
- Critérios de aceite sempre em formato de checklist acionável

---

## Exemplo de Invocação

```
/handoff checkout flow mobile
```

**Output esperado:**
Feature: Checkout — Pagamento  
Objetivo: Permitir que o usuário conclua o pagamento com segurança.  
Fluxo: Selecionar método → Inserir dados do cartão → Confirmar compra  
Componentes: seletor de pagamento, formulário de cartão, botão CTA  
Validações: cartão obrigatório, validade obrigatória  
Estados: cartão inválido, carregando pagamento, confirmação de sucesso  
Critério de aceite: pagamento concluído sem reload de página.
