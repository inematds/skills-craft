# Criando Agent Skills — Do Catálogo à Sua Primeira Skill

Curso **data-driven** sobre Agent Skills, no formato [INEMA.CLUB](https://inema.club).
Em vez de teoria solta, parte de uma **análise real de 39.366 skills** coletadas do [skills.sh](https://skills.sh).

🔗 **Curso publicado:** https://inematds.github.io/skills-craft/

## O que tem aqui

| Caminho | O que é |
|---|---|
| `index.html` | Landing do curso |
| `curso/trilha1..5/` | 5 trilhas × (índice + 2 módulos) = 16 páginas |
| `data/` | Dataset coletado do skills.sh (metadados das 39k skills, grupos, stats) |
| `corpus/examples/` | 25 arquivos `SKILL.md` reais das melhores skills (1 a 2 por grupo) |
| `BUILD-SPEC.md` | Spec de design usado para gerar as páginas no padrão INEMA |

## As 5 trilhas

1. 🌍 **Panorama do Ecossistema** — o que é uma skill, por que o formato venceu, o mapa do skills.sh.
2. ⭐ **Qualidade & As Melhores** — como ler sinais de qualidade e vitrine das melhores por grupo.
3. 🧬 **Anatomia de uma Skill** — SKILL.md por dentro, progressive disclosure, a description que dispara.
4. 🛠️ **Como Criar (o loop)** — do intent ao draft, e o loop testar→avaliar→iterar.
5. 🧠 **O Que Pensar** — quando vale uma skill, anti-padrões, publicar/versionar/medir.

## Os dados (`data/`)

- `skills-index.json` — as 39.366 skills (id, name, installs, source, group).
- `sources.json` — 5.075 repositórios fonte com contagem.
- `by-group-top30.json` — top 30 por grupo.
- `selection-details.json` — 177 skills top com a `description` real.
- `stats.json` — estatísticas agregadas (lei de potência, distribuição, volume por grupo).

### Números-chave
- **39.366** skills · **5.075** repos · **53,9M** instalações somadas · **16** grupos.
- Lei de potência: **60,2%** têm <100 installs; só **0,3% (131)** passam de 100k.
- As **100 mais instaladas** concentram **43,7%** de todos os installs.

> Coleta via API pública do skills.sh (`/api/search`) + `raw.githubusercontent` para os `SKILL.md`. Snapshot de 2026-06.

---

Feito para o portal [INEMA.CLUB](https://inema.club) · 2026
