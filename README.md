# ai-lab

Une équipe d'agents Claude qui écrit un papier de recherche IA en LaTeX à partir des résultats de ton projet.

## Installation (dans le projet de recherche)

    /plugin marketplace add NicolasDrapier/ai-lab
    /plugin install ai-lab@ai-lab --scope project

Pour que toute l'équipe l'ait automatiquement, commite dans `.claude/settings.json` du projet :

    {
      "extraKnownMarketplaces": {
        "ai-lab": { "source": { "source": "github", "repo": "NicolasDrapier/ai-lab" } }
      },
      "enabledPlugins": { "ai-lab@ai-lab": true }
    }

Mise à jour : `/plugin marketplace update ai-lab` (pense à incrémenter `version` dans `plugin.json`).

Prérequis : `latexmk`, `uv`, et les skills `no-ai-slop` et `humanizer`.

## Utilisation

1. Dépose le template LaTeX de la venue dans `template/` (avec son `main.tex`).
2. `/grill-me` : ajoute `Edit(paper/**)` et `Edit(.ai-lab/**)` à `.claude/settings.json`, puis interview → `.ai-lab/brief.md`.
3. `/write-paper` : Hawking orchestre l'équipe → `paper/main.pdf`.

## L'équipe

| Agent | Rôle |
|---|---|
| Hawking (`/write-paper`) | chef d'orchestre : plan, dispatch, compilation, rapport |
| results-analyst | extrait les chiffres avec leur source → `.ai-lab/findings.md` |
| figure-maker | figures matplotlib + tables booktabs → `paper/assets/` |
| bibliographer | `paper/refs.bib`, chaque référence vérifiée en ligne |
| section-writer | une section `paper/sections/NN_nom.tex`, passée à `no-ai-slop` |
| reviewer | review façon venue + `humanizer` → `.ai-lab/review.md` |

## Arborescence produite

    template/     # ton template, jamais modifié
    paper/        # copie de template/ : main.tex, refs.bib, sections/, assets/
    .ai-lab/      # brief, findings, outline, review
