👉 **un algorithme de scoring de l’ambiguïté et de la validation**, **applicable a priori** sur un **SprintContract (C)**, **avant toute exécution**, et **cohérent avec `task_plan.md`** .

Je respecte strictement ta méthode : **pipeline → concret → mesurable → humain-compréhensible**.  
Pas de storytelling. Pas de morale. Pas de raccourci.

---

# ALGORITHME DE SCORING

## μ(ambiguïté) et μ(validation) pour un SprintContract (C)

---

## 0) Ontologie minimale

On évalue **un objet C** composé de trois sous-objets **déjà stabilisés** :

- $(G) = Sprint Goal$
- $(B = {b_1,\dots,b_n}) = Sprint Backlog$
- $(D = {d_1,\dots,d_m}) = Definition of Done$
Chaque score est **local**, puis **agrégé**.

---

## 1) Ensembles de mesure

### Ambiguïté
$\mathcal{A} = \mathcal{A}_G \cup \mathcal{A}_B \cup \mathcal{A}_D$  

### Validation
$\mathcal{V} = \mathcal{V}_G \cup \mathcal{V}_B \cup \mathcal{V}_D$  
Chaque composante retourne une valeur **dans ([0,1])**.

---

## 2) Logique générale (principe de calcul)
- **μ(ambiguïté)** = proportion de zones **interprétables**
- **μ(validation)** = proportion de zones **vérifiables sans discussion**

👉 Important :  
Ces scores ne sont **pas opposés mathématiquement**.  
Un contrat peut être **peu ambigu mais peu validable**, ou l’inverse.

---

## 3) Scoring du Sprint Goal

### 3.1 Ambiguïté du Goal
On évalue **4 critères binaires** (0 = OK, 1 = problème).

|Critère|Question concrète|
|---|---|
|A₁|Le Goal contient-il un mot flou ? (“améliorer”, “optimiser”, “simple”, etc.)|
|A₂|Le Goal contient-il plus d’**un** verbe d’action ?|
|A₃|Le résultat final peut-il être interprété de 2 manières ?|
|A₄|La preuve n’est pas explicitement nommée ?|

$$
mu_A(G)=\frac{A_1+A_2+A_3+A_4}{4}
$$

---

### 3.2 Validation du Goal

|Critère|Condition|
|---|---|
|V₁|Une preuve **unique** est mentionnée|
|V₂|La preuve est **binaire** (URL/commande/fichier)|
|V₃|Un tiers peut vérifier en < 2 minutes|

$$
\mu_V(G)=\frac{V_1+V_2+V_3}{3}
$$

---

## 4) Scoring du Sprint Backlog

### 4.1 Ambiguïté du Backlog
Pour chaque item (b_i) :

|Critère|Test|
|---|---|
|A₁|L’item est-il un **thème** et non une action ?|
|A₂|L’item peut-il donner lieu à >1 Phase possible ?|
|A₃|La taille n’est pas implicitement bornée ?|

Score local :  

$$
mu_A(b_i)=\frac{A_1+A_2+A_3}{3}
$$

Score global :  

$$
\mu_A(B)=\frac{1}{n}\sum_{i=1}^n \mu_A(b_i)
$$

---

### 4.2 Validation du Backlog

Un backlog est **validable** s’il est **structurellement compilable** vers `task_plan.md` .
Critères globaux :

|Critère|Test|
|---|---|
|V₁|(|
|V₂|Ordre strict conservable|
|V₃|Chaque item contribue à **au moins un** critère de DoD|
$$
\mu_V(B)=\frac{V_1+V_2+V_3}{3}
$$

---

## 5) Scoring de la Definition of Done (DoD)

### 5.1 Ambiguïté de la DoD

Pour chaque (d_j) :

|Critère|Test|
|---|---|
|A₁|Contient-il un jugement humain non borné ?|
|A₂|Contient-il plusieurs preuves mélangées ?|
|A₃|La preuve n’est pas directement exécutable ?|


$$
\mu_A(d_j)=\frac{A_1+A_2+A_3}{3}$  $\quad\Rightarrow\quad\mu_A(D)=\frac{1}{m}\sum \mu_A(d_j)
$$


---

### 5.2 Validation de la DoD

Chaque critère DoD appartient à un type ({URL, CMD, ART, REP, H})  
(cf. structure formalisée précédemment).

| Critère | Condition                                     |
| ------- | --------------------------------------------- |
| V₁      | ≥1 critère **automatique** (URL ou CMD)       |
| V₂      | Toutes les preuves sont traçables             |
| V₃      | La DoD est indépendante de l’ordre des Phases |

$$
 \mu_V(D)=\frac{V_1+V_2+V_3}{3}  
$$

---

## 6) Agrégation finale (SprintContract C)

### Ambiguïté globale


$$
\mu_A(C)=\frac{\mu_A(G)+\mu_A(B)+\mu_A(D)}{3}  
$$

### Validation globale

$$
\mu_V(C)=\frac{\mu_V(G)+\mu_V(B)+\mu_V(D)}{3}  
$$

---

## 7) Seuils opérationnels (non normatifs, mais utilisables)

| Zone                        | Interprétation             |
| --------------------------- | -------------------------- |
| $(\mu_A(C) < 0.25)$         | Contrat **stable**         |
| $(0.25 \le \mu_A(C) < 0.5)$ | Contrat **fragile**        |
| $(\mu_A(C) \ge 0.5)$        | Contrat **non compilable** |

| Zone                       | Interprétation           |
| -------------------------- | ------------------------ |
| $(\mu_V(C) \ge 0.7)$       | Validation **robuste**   |
| $(0.4 \le \mu_V(C) < 0.7)$ | Validation **partielle** |
| $(\mu_V(C) < 0.4)$         | Validation **faible**    |

---

## 8) Cohérence avec ta topologie C → Fp

- Un **bon C** (μA bas, μV haut)  
    ⇒ compile vers un `task_plan.md` **court, stable, non narratif**
- Un **mauvais C**  
    ⇒ produit un plan bavard, instable, qui viole les seuils de stabilité que tu as définis

👉 L’algorithme agit donc comme **filtre a priori**, avant même Scrum.

---

### État du système maintenant

Tu disposes :

1. d’un **format canonique** de C (Goal, Backlog, DoD)
2. d’un **mapping commutatif** vers `task_plan.md
3. d’un **algorithme de scoring** applicable **avant exécution**
