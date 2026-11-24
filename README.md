# Proximo UCC 🎓

Plateforme (PWA) permettant aux étudiants de l'UCC de **commander à manger depuis leur auditoire** auprès
d'étudiants-vendeurs, qui livrent sur place. Application mobile-first, minimaliste, style Uber.

## Structure du dépôt
```
proximo/
├── AGENTS.md              ← règles de l'agent de code (lire en premier)
├── CLAUDE.md              ← pointe vers AGENTS.md
├── docs/
│   ├── PROGRESS.md        ← avancement : une tâche à la fois
│   ├── DECISIONS.md       ← décisions figées + journal
│   ├── specs/             ← spécifications (vision, règles métier, API, modèle, UI, plan 2D…)
│   │   └── data/auditoires.json   ← données PROVISOIRES du plan 2D
│   └── workflow/
│       ├── 00-workflow.md           ← comment l'agent travaille, étape par étape
│       ├── PROMPT-DEMARRAGE.md      ← le message à donner à l'agent à chaque session
│       └── tasks/T00 … T20          ← une fiche par tâche
├── backend/               ← Spring Boot (créé à la tâche T01)
└── frontend/              ← React + Vite (créé à la tâche T13)
```

## Pour l'auteur : comment travailler avec l'agent
1. `git init`, premier commit de ce dossier, dépôt GitHub distant.
2. Ouvre une **nouvelle session** de l'agent à chaque tâche.
3. Colle le contenu de `docs/workflow/PROMPT-DEMARRAGE.md`.
4. Relis le résultat et lance la commande de vérification de la tâche. Si tout est bon, passe à la suivante.
