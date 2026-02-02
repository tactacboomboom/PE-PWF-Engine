# ENRICHISSEMENT DU MAPPING $(C \rightarrow task_plan.md)$

## 1) Ensembles (ce qui est projeté vs ce qui est généré)

- **Projeté (sans invention)** depuis C :
    - Goal
    - Backlog (ordre, cardinalité)
    - DoD (contraintes globales)

- **Généré (résidu d’exécution, hors C)** dans Fp :
    - Key Questions
    - Decisions Made
    - Errors Encountered
    - Notes & Rappels

**Règle clé** : tout champ généré **ne doit jamais rétroagir sur C** (anti-dérive).

---

## 2) Logique (opérateurs explicites)

On définit trois opérateurs, séparés :
1. **Compile** $(f_2)$ :  
$$
    f_2(C) \Rightarrow F_p^{\text{structure}}  
$$
    (structure uniquement, sans contenu inventé)

2. **Hydrate** $(h)$ :  
$$
    h(F_p^{\text{structure}}, \text{exécution}) \Rightarrow F_p^{\text{vivant}}
$$
    (ajoute Questions/Décisions/Erreurs)

3. **Validate** $(v)$ :  
$$
    v(F_p, C) \Rightarrow {\text{done}, \text{not done}}
$$
    (DoD comme barrière globale)

**Interdit** : $(h \circ f_2)$ ne doit pas modifier les éléments projetés.

---

## 3) Invariants (anti-ambiguïté)

- **Bijection stricte** :  
	|Backlog| = |Phases|  

- **Ordre conservé** : backlog #i → phase #i
- **Status borné** : `pending | in_progress | complete` uniquement
- **DoD non locale** : aucune Phase ne “valide” la DoD seule

---

## 4) Axes de variation (autorisés)
- Granularité des **tâches** à l’intérieur d’une Phase (pas des Phases)
- Nombre de **Key Questions** (≤ 3 actives)
- Nombre de **Decisions** (journal, pas design doc)
- Nombre d’**Errors** (borné par 3-Strike)

---

## 5) Analyse (seuils / stabilité)

### Seuil d’instabilité (à éviter)
- Une Phase contient du narratif (“comprendre”, “réfléchir”)
- Les Key Questions ressemblent à des objectifs (“comment bien faire…”)
- Decisions deviennent des essais (doivent être des choix actés)
- Errors sans mutation explicite au Strike suivant

### Seuil de stabilité (cible)
- Chaque Phase = liste de **tâches actionnables**
- Chaque Question = **bloquante** pour avancer
- Chaque Decision = **irréversible à court terme**
- Chaque Error = **différente** de la précédente (3-Strike respecté)

---

## 6) Catégories (cohérence interne)

### Mapping canonique (table)

|Élément C|Élément Fp|Règle d’enrichissement|
|---|---|---|
|Sprint Goal|Goal|Copie stricte (1 ligne)|
|Backlog #i|Phase i (titre)|Verbe + objet, sans thème|
|—|Tâches de Phase|Décomposition locale (hors C)|
|DoD|Status `complete`|Interdit tant que DoD non satisfaite|
|—|Key Questions|Uniquement incertitudes bloquantes|
|—|Decisions Made|Choix + rationnel concis|
|—|Errors Encountered|3-Strike, mutation obligatoire|

---

## 7) Topologie (flux opératoire humain-compréhensible)

1. **Humain spécifie C** (Goal, Backlog, DoD)
2. **Compile** → création de `task_plan.md` **structurel**
3. **Humain/Agent exécute** une Phase à la fois
4. **Hydrate** Fp (questions, décisions, erreurs)
5. **Validate** via DoD (global)
6. **Si échec au Strike 3** → renégociation de C (seul point de rétroaction autorisé)

---

## 8) Probabilités / Mesure (pré-algo futur)

**Réduction d’ambiguïté** obtenue par :
- séparation stricte projection / exécution
- interdiction de rétroaction Fp → C
- bornage des champs générés

**Augmentation de validation** obtenue par :
- DoD globale, non fractionnée
- preuves dures (URL/CMD/ART/REP)
- traçabilité des erreurs (M3)

---

## Cible formelle (ce que tu construis)

> **Un compilateur d’intention** :
> - entrée : Contrat C **a priori** (avant Scrum)
> - sortie : `task_plan.md` **exécutable**
> - propriété : toute réussite dans Fp est **équivalente** à la satisfaction de C (commutativité)

Le raisonnement reste **humain-compréhensible** parce que :

- chaque champ a une fonction unique
- chaque enrichissement est local et journalisé
- l’échec est un **signal**, pas une faute
