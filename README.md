# 🎨 Figma Handoff Skill — Claude AI

Uma skill para [Claude.ai](https://claude.ai) que transforma telas do Figma em documentação técnica completa de handoff para times de engenharia, produto e QA — usando o MCP do Figma diretamente.

---

## ✨ O que essa skill faz

Conectada ao MCP do Figma, ela lê frames, componentes, layouts e lógica de navegação e gera automaticamente:

- 📋 **Documentação técnica** de cada tela (componentes, specs, regras funcionais)
- 🔄 **Mapa de fluxo** de navegação entre telas
- 🧩 **Auditoria de componentes** e oportunidades de design system
- ⚠️ **Detecção de gaps de UX** (estados ausentes, inconsistências, ações ambíguas)
- 📝 **PRD curto** pronto para Jira ou Linear
- ✅ **Critérios de aceite** em checklist acionável

---

## 🚀 Instalação

### Opção 1 — Instalar o arquivo `.skill` diretamente

1. Faça download do arquivo [`figma-handoff.skill`](./figma-handoff.skill)
2. Acesse [claude.ai](https://claude.ai)
3. Vá em **Configurações → Skills**
4. Clique em **"Instalar skill"** e selecione o arquivo baixado

### Opção 2 — Instalar manualmente pela pasta

1. Clone este repositório:
   ```bash
   git clone https://github.com/seu-usuario/figma-handoff-skill.git
   ```
2. Copie a pasta `figma-handoff/` para o diretório de skills do Claude
3. Reinicie o Claude para carregar a skill

---

## 📋 Pré-requisitos

- Conta no [Claude.ai](https://claude.ai) (Pro ou superior recomendado)
- **MCP do Figma conectado** nas configurações de ferramentas do Claude
  - Acesse: Configurações → Ferramentas → Figma MCP → Conectar
- Arquivo Figma com permissão de leitura

---

## 💬 Como usar

Com a skill instalada e o Figma MCP conectado, cole o link do seu arquivo Figma e use um dos comandos:

### Comandos disponíveis

| Comando | O que gera |
|---|---|
| `/handoff` | Documentação técnica completa de todas as telas |
| `/flow-map` | Mapa de navegação e fluxo de usuário |
| `/component-audit` | Inventário de componentes e design system |
| `/ux-gaps` | Tabela de gaps: estados ausentes e inconsistências |
| `/dev-ready` | Spec enxuta pronta para engenharia |
| `/prd-short` | PRD resumido para Jira / Linear |

### Exemplo de uso

```
/handoff https://www.figma.com/design/ABC123/meu-app?node-id=0-1
```

Ou simplesmente cole o link e peça:

```
Faça o handoff completo desse arquivo do Figma:
https://www.figma.com/design/ABC123/meu-app
```

---

## 📄 Exemplo de output

O handoff gerado inclui para cada tela:

```markdown
# Feature Name

## Objetivo
O que esta tela resolve para o usuário.

## Fluxo Principal do Usuário
1. Passo a passo...

## Componentes de UI
| Componente | ID | Dimensões | Notas |
|---|---|---|---|

## Regras Funcionais
- Lógica de comportamento

## Regras de Validação
| Campo | Obrigatório | Formato | Erro |

## Estados
Default / Hover / Focus / Error / Success / Disabled

## Critérios de Aceite
- [ ] Checklist acionável
```

Veja um [exemplo completo de output](./examples/handoff-exemplo.md) gerado a partir de um arquivo real.

---

## 📁 Estrutura do repositório

```
figma-handoff-skill/
├── README.md                  # Este arquivo
├── figma-handoff.skill        # Arquivo de instalação da skill
├── figma-handoff/
│   └── SKILL.md               # Instruções da skill para o Claude
└── examples/
    └── handoff-exemplo.md     # Exemplo de output gerado
```

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:

- Abrir uma **issue** com sugestões ou bugs
- Enviar um **pull request** com melhorias na skill
- Compartilhar exemplos de outputs na pasta `examples/`

---

## 📜 Licença

MIT — use, modifique e distribua livremente.

---

## 🙏 Créditos

Desenvolvido por Alexandre Santos com [Claude AI](https://claude.ai) e o sistema de Skills da Anthropic.  
Integração via [Figma MCP](https://www.figma.com/developers/mcp).
