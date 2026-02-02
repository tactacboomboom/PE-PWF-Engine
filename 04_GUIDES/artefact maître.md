# Canevas canonique du pipeline de sprint

Ce canevas synthétise **l’ensemble du système** en une vue unique, lisible par un humain **et** exploitable par un LLM, sans explication orale.

---

## 0. Ontologie minimale

**Objets**

- **C** : Contrat de Sprint = (Goal, Backlog, DoD)
    
- **Fp** : task_plan.md (plan exécutable)
    
- **Fn** : findings.md (apprentissages)
    
- **R** : progress.md (preuves)
    

**Morphismes**

- f₁ : Intention clarifiée → Contrat de Sprint
    
- f₂ : Contrat de Sprint → task_plan.md (Compilation)
    
- f₃ : (task_plan, findings, progress) → Validation finale
    

**Invariant global**

- Le Contrat et le Plan décrivent le **même objet**, à deux niveaux différents.
    

---

## 1. Entrée humaine (hors contrat)

### Intention brute (H)

- Formulation libre
    
- Non fiable
    
- Non contractuelle
    

### Intention clarifiée (IC)

Produit via questionnaire (Prompt 0).

**Questions minimales**

1. Quel résultat final observable veux-tu obtenir ?
    
2. Quelle preuve unique permet de dire « c’est réussi » ?
    
3. Qui utilise ou bénéficie de ce résultat ?
    
4. Qu’est-ce qui ne doit PAS être fait dans ce sprint ?
    
5. Délai maximal accepté ?
    

**Sortie** : Bloc IC structuré.

---

## 2. Génération du Contrat de Sprint (Prompt 1)

**Entrées obligatoires**

- Intention clarifiée (IC)
    
- ITEM 1 — GOAL.md
    
- ITEM 2 — SPRINT BACKLOG.md
    
- ITEM 3 — DEFINITION OF DONE.md
    

**Sortie** : `CONTRAT_DE_SPRINT.md`

### Structure canonique

#### Sprint Goal

- 1 phrase
    
- 1 verbe
    
- 1 objet
    
- 1 preuve unique
    

#### Sprint Backlog

- 2 à 5 items max
    
- Chaque item = verbe + objet précis
    
- Chaque item deviendra UNE phase
    

#### Definition of Done

- 2 à 5 critères
    
- Chaque critère = 1 preuve (URL | CMD | ART | REP)
    
- Au moins 1 critère automatique
    

---

## 3. Évaluation d’ininterprétabilité (Prompt 2)

**Entrées obligatoires**

- CONTRAT_DE_SPRINT.md
    
- ALGORITHME_DE_SCORING.md
    

**Sorties**

- μ(ambiguïté)
    
- μ(validation)
    
- Verdict : ACCEPTABLE | FRAGILE | NON-COMPILABLE
    

**Règle de passage**

- Si μ(ambiguïté) ≥ seuil → STOP
    

---

## 4. Compilation vers task_plan.md (Prompt 3)

**Entrée**

- CONTRAT_DE_SPRINT.md validé
    

**Règles de compilation**

- Goal copié strictement
    
- Backlog item i → Phase i
    
- Ordre conservé
    
- DoD ne devient pas une Phase
    

### Structure d’une Phase

- 2 à 5 tâches actionnables
    
- Tâches = implémentation locale (non contractuelle)
    
- Ligne obligatoire : documenter dans findings.md
    
- Status : pending | in_progress | complete
    

---

## 5. Exécution et hydratation

### task_plan.md (Fp)

- Contient : Phases, tâches, Key Questions, Decisions, Errors
    

**Key Questions**

- Incertitudes bloquantes découvertes pendant l’exécution
    
- Disparaissent une fois résolues
    

**Errors Encountered (3-Strike)**

- Même erreur ≠ même tentative
    
- Obligation de mutation
    

### findings.md (Fn)

- Décisions techniques
    
- Issues & blocages
    
- Mémoire non prescriptive
    

### progress.md (R)

- Actions réalisées
    
- Fichiers modifiés
    
- Résultats des tests
    
- Journal des erreurs horodaté
    

---

## 6. Validation finale

**Condition de succès du sprint**

- Toutes les Phases = complete
    
- Toutes les preuves DoD satisfaites
    
- Tests réels conformes aux attentes
    

**Sortie**

- Sprint validé ou non validé
    

---

## 7. Mesures de discipline (hors contrat)

- **M1** : Évitement des erreurs déjà notées (via Journal des erreurs)
    
- **M2** : Densité d’apprentissage (findings / heure)
    
- **M3** : Diminution des erreurs récurrentes
    

Ces mesures évaluent **la qualité de l’exécution**, jamais le Contrat.

---

## 8. Principe directeur

> Le système est correct si :
> 
> - Un autre humain ou un autre LLM peut exécuter le sprint
>     
> - Sans explication orale
>     
> - En comprenant quoi faire, quoi noter, et quand c’est fini
>
