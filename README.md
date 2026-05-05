<div align="center">

# Laws of UX para Claude Code

**3 skills que trazem as 30 Leis de UX direto pro seu fluxo de desenvolvimento.**

Pare de sentir que falta algo na sua interface. Receba feedback acionável, baseado em ciência cognitiva, com o código já pronto pra colar.

[![License: MIT](https://img.shields.io/badge/license-MIT-amber.svg)](./LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-skills-orange.svg)](https://docs.claude.com/en/docs/claude-code/skills)
[![PT-BR](https://img.shields.io/badge/docs-PT--BR-green.svg)](#)

</div>

---

## ⚡ O que faz

Você tá codando uma tela. Pede pro Claude analisar. Ele responde:

> _"O botão 'Trocar plano' tá pequeno (28px) — viola **Lei de Fitts**. Aumenta pra 40×40 mínimo: `style={{ height: 40, padding: '0 16px' }}` em `AccountScreen.tsx:289`. Também tem 5 ações na mesma linha — **Lei de Hick** sugere agrupar em até 3."_

Não é dica genérica. É **arquivo:linha + diff pronto**.

## 📦 As 3 skills

<table>
<tr>
<td width="33%" valign="top">

### 🧭 `laws-of-ux`
**Modo conselheiro**

Use **enquanto você constrói**.

Analisa o componente, escolhe quais das 30 leis se aplicam, sugere mudanças de código.

```
/laws-of-ux
```

</td>
<td width="33%" valign="top">

### 🔍 `laws-of-ux-review`
**Auditoria completa**

Use **depois da feature pronta**.

Pontua de 0 a 60, classifica achados em Crítico/Alerta/Sugestão, entrega plano de ação priorizado.

```
/laws-of-ux-review
```

</td>
<td width="33%" valign="top">

### ✅ `laws-of-ux-checklist`
**Pre-ship rápido**

Use **antes do merge**.

12 pontos de pass/fail cobrindo Fitts, Doherty, Hick, Cognitive Load, Jakob's Law. Veredito claro: pode subir ou não.

```
/laws-of-ux-checklist
```

</td>
</tr>
</table>

## 🎯 Por que vale a pena

A maioria de "audit de UX" trava em um dos dois extremos:

❌ **Vago demais** — "melhorar descoberta" / "reduzir atrito" sem código  
❌ **Checklist seca** — passa/falha sem explicar o porquê

**Aqui é diferente.** Cada achado vem com:

- 🧠 **Qual Lei de UX** está sendo violada (com explicação 1-linha)
- 📍 **Onde no código** (`arquivo.tsx:42`)
- 🛠 **O que mudar** (diff ou rewrite pronto)
- 🎯 **Por que importa** (impacto real no usuário)

## 📊 Caso de uso real

Usado em produção no [Core Educação](https://corestudio.ai), num SaaS B2B multi-tenant de WhatsApp + IA com usuários **leigos** (donos de negócio sem time técnico).

**Resultado em 1 semana:** ~50 fixes shipped, score estimado subiu de **C+ (38/60)** pra **A (58/60)**.

Achados que essas skills pegaram:

| Antes | Depois |
|-------|--------|
| 8 modais nativos `window.confirm()` espalhados | Componente único `ConfirmModal` com tom Core |
| PeriodPicker que ciclava (2 cliques pra ir 7d→90d) | Segmented control: 1 click qualquer direção |
| Audit log mostrando `event_type: "provider_fallback_used"` | "Provedor principal falhou — usamos backup" |
| Onboarding perdia tudo no F5 | Persistência em `localStorage` automática |
| Hint de atalhos visível pra leigos que nunca usam | Aparece só após primeira tecla power-user |
| KB com "chunks" everywhere (jargão) | "Trechos" em toda UI visível |
| 3 botões confusos no Inbox (`Assumir`/`Assumir pra mim`/`Resolver`) | 2 botões claros (`Assumir conversa` + `Encerrar`) |

## 🚀 Como instalar

### Opção 1 — Pessoal (no seu Claude Code)

```bash
git clone https://github.com/keysjoao/laws-of-ux-skills.git
cp -r laws-of-ux-skills/laws-of-ux* ~/.claude/skills/
```

Reinicia o Claude Code. Pronto, é só usar.

### Opção 2 — Time / projeto compartilhado

Adiciona como submódulo dentro do projeto:

```bash
cd seu-projeto
git submodule add https://github.com/keysjoao/laws-of-ux-skills.git .claude/skills/_laws-of-ux
```

Quem rodar Claude Code dentro do repo já pega as 3 skills automaticamente.

### Opção 3 — Download direto

Vai em [Releases](https://github.com/keysjoao/laws-of-ux-skills/releases), baixa o ZIP, extrai pra `~/.claude/skills/`.

## 🎮 Como usar

Depois de instalado, dentro do Claude Code:

```bash
# Modo conselheiro — enquanto você constrói
/laws-of-ux

# Auditoria completa de uma página/componente
/laws-of-ux-review src/components/Dashboard.tsx

# Checklist rápido pre-merge
/laws-of-ux-checklist
```

**Bônus:** as skills auto-disparam quando você menciona termos como _"audit de UX"_, _"review UX"_, _"check UX"_, _"pode dar deploy?"_, _"design review"_. Não precisa decorar comando.

## 📚 As 30 Leis (referência)

Aesthetic-Usability · Chunking · Cognitive Bias · Cognitive Load · Common Region · **Doherty Threshold** · **Fitts's Law** · Flow · Goal-Gradient · **Hick's Law** · **Jakob's Law** · Law of Pragnanz · Law of Proximity · Law of Similarity · Law of Uniform Connectedness · Mental Model · **Miller's Law** · Occam's Razor · Paradox of Choice · Pareto Principle · Parkinson's Law · **Peak-End Rule** · Postel's Law · Selective Attention · Serial Position Effect · **Tesler's Law** · Von Restorff Effect · Working Memory · Zeigarnik Effect

> Conteúdo completo de cada lei em [`laws-of-ux/references/ux-laws-complete.md`](./laws-of-ux/references/ux-laws-complete.md).
> 
> As **leis em negrito** são as mais frequentes em audits — vale dar uma olhada nelas mesmo se você nunca abriu o repo.

## 🤝 Contribuindo

Achou um caso que a skill não cobriu? Manda PR.

Os arquivos são markdown puro — nada de compilar, instalar dependência, configurar build. Edita, salva, abre PR.

Se você usar essas skills num projeto e fizer um fix legal, abre uma issue contando — ajuda a calibrar os triggers.

## 📜 Licença

[MIT](./LICENSE) — pode usar comercial, pode modificar, pode redistribuir. Só mantém o crédito.

## 🙏 Créditos

- **30 Leis de UX** e suas formulações: [Jon Yablonski](https://lawsofux.com) — vai lá no site dele, vale o tempo
- **Formato Skills**: [Anthropic Agent Skills standard](https://docs.claude.com/en/docs/claude-code/skills)
- **Empacotador**: [@keysjoao](https://github.com/keysjoao) — battle-tested no [Core Educação](https://corestudio.ai)

## 🔗 Skills companions

Se você curtiu essas, dá uma olhada também em:

- ♻️ [**poo-skills**](https://github.com/keysjoao/poo-skills) — 3 skills DRY/SOLID que impedem o Claude de criar código duplicado (prevention, audit, refactor)

---

<div align="center">

**Se essas skills economizarem 10 minutos do seu dia, dá uma ⭐ no repo.**

[Reportar bug](https://github.com/keysjoao/laws-of-ux-skills/issues) · [Sugerir lei nova](https://github.com/keysjoao/laws-of-ux-skills/issues) · [Ver no GitHub](https://github.com/keysjoao/laws-of-ux-skills)

</div>
