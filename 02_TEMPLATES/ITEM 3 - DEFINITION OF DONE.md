# ITEM #3 — DEFINITION OF DONE (DoD)

## 1) Ensembles

Définissons l’ensemble des critères DoD valides :

$$
[  
\mathcal{D}={d_i \mid d_i \text{ est vérifiable, indépendant, et observable}}  
]
$$

Sous-ensembles (types de preuves) :
- $(\mathcal{D}_{URL})$ : preuve par **URL/endpoint** accessible
- $(\mathcal{D}_{CMD})$ : preuve par **commande** (tests/lint/build)
- $(\mathcal{D}_{ART})$ : preuve par **artefact** (fichier généré)
- $(\mathcal{D}_{REP})$ : preuve par **repo** (commit/hash/diff)
- $(\mathcal{D}_{H})$ : **validation humaine** (signature)

> Règle : une DoD **doit** appartenir à **un seul** sous-ensemble (typage exclusif).

---

## 2) Logique (opérateurs)

La DoD n’explique pas _comment_ faire, elle définit **comment décider que c’est fini**.

Opérateurs nécessaires :
- $(\textsf{check}(d_i)\rightarrow{\text{pass},\text{fail}})$
- $(\textsf{evidence}(d_i)\rightarrow\text{lien/commande/artefact})$

Contrôle de complétude :

$$
[  
\textsf{Done}(C) \iff \bigwedge_i \textsf{check}(d_i)=\text{pass}  
]
$$
Aucune agrégation floue. **ET logique strict**.

---

## 3) Invariants (non négociables)

1. **Chaque critère DoD a UNE preuve principale** (pas “URL + tests + feeling”).
2. **Aucun mot narratif** (“correct”, “propre”, “documenté” sans support).
3. **La DoD est stable hors contexte** : un tiers peut valider sans te parler.
4. **La DoD ne dépend pas de l’ordre des Phases** (elle valide le résultat final).

---

## 4) Axes de variation (autorisés)

- Type de preuve (URL vs CMD vs ART vs REP vs H)
- Nombre de critères (idéal : 2 à 5)
- Degré d’automatisation (0–100%)

> Interdit : mélanger plusieurs preuves dans un même critère.

---

## 5) Analyse (seuils / stabilité)

### Seuil d’instabilité
Un critère est **instable** si :
- la preuve n’est pas directement exécutable/clicable
- il dépend d’un jugement (“lisible”, “à jour”, “clair”)
- il dépend d’un futur non borné (“sera monitoré”, “sera optimisé”)

➡️ Dans ces cas, $(\mu(\text{ambiguïté})\uparrow)$.

### Seuil de stabilité
Un critère est **stable** si :
- la preuve est **immédiate** (URL, commande, fichier)
- la vérification prend **< 1 minute**
- le résultat est **binaire**

---

## 6) Catégories (cohérence interne)

On impose **5 catégories exclusives**.  
Chaque DoD doit être étiquetée.

### D1 — URL

> Validation par accès externe

```
[D1] URL <https://…> loads and displays expected content
```

### D2 — Commande

> Validation par exécution locale/CI

```
[D2] `npm test` returns exit code 0
```

### D3 — Artefact

> Validation par existence/conformité d’un fichier

```
[D3] File `dist/report.json` exists and matches schema
```

### D4 — Repo

> Validation par traçabilité Git

```
[D4] Commit <hash> pushed to main branch
```

### D5 — Humain

> Validation disciplinaire (jamais seule)

```
[D5] Human signature recorded (date + name)
```

> Règle dure : **D5 ne peut jamais être le seul critère**.

---

## 7) Topologie (mapping C → Fp)

**Mapping sans invention** :
- DoD (C) **ne devient pas** une Phase
- DoD **contraint** le statut `complete` de Fp
- Une Phase ne peut passer à `complete` **que si** elle ne rend pas la DoD impossible

Dans `task_plan.md`, la DoD agit comme :
- une **barrière globale de sortie**
- une **source de checks finaux** consignés dans `progress.md`

---

## 8) Probabilités / mesure (pré-scoring futur)

### Ambiguïté ↑ si :
- le critère commence par “Documentation…”
- la preuve n’est pas nommée
- plusieurs verbes dans un critère

### Validation ↑ si :
- la preuve est automatique (CMD/URL)
- la preuve est reproductible
- la preuve est indépendante du contexte humain

---

## Format minimal de DoD (template final)

À coller dans `CONTRAT_DE_SPRINT.md`

```
## ✅ Definition of Done (DoD)

- [D?] <critère binaire> — PROOF: <commande | URL | fichier | commit>
- [D?] <critère binaire> — PROOF: <commande | URL | fichier | commit>
```

### Exemples concrets

**Bon**

```
- [D1] Public URL is reachable — PROOF: https://myapp.vercel.app
- [D2] All tests pass — PROOF: `npm test`
- [D4] Changes pushed — PROOF: commit hash abc123
```

**Mauvais**

```
- App works correctly
- Code is clean
- Documentation updated
```

---

## Tensions signalées (sans les résoudre pour toi)
- Plus la DoD est **automatisée**, plus (\mu(\text{validation})\uparrow),  
    mais plus l’intention doit être cadrée en amont (Goal/Backlog).
- Une DoD trop courte est fragile, trop longue devient bureaucratique.
- La validation humaine est nécessaire pour la discipline, insuffisante pour la preuve.

---

## Résultat net pour la DoD

- $(\mu(\text{ambiguïté}))$ : **faible**, si typage + preuve imposés
- $(\mu(\text{validation}))$ : **élevé**, surtout avec URL/CMD
- Mapping vers `task_plan.md` : **indirect mais strict** (contrainte globale)
