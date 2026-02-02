# 📖 GLOSSAIRE UNIFIÉ (CPE ↔ PWF)

Ce document lie l'ontologie de la **Canonical Pipeline Equation (CPE)** aux fichiers concrets de la méthode **Planning-With-Files (PWF)**.

| Symbole CPE | Nom du Fichier PWF | Rôle et Finalité |
| :--- | :--- | :--- |
| **𝕀₀** | `01_INTENTION_BRUTE.md` | **Intention brute** : Texte libre, non structuré et non validé [2, 4]. |
| **𝕮ₙ** | `02_CONTRAT_DE_SPRINT.md` | **Contrat** : Commande testable (Goal, Backlog, DoD). Source de vérité décisionnelle [2, 5]. |
| **𝕊ₙ** | `03_TASK_PLAN.md` | **Sprint** : Instance opérationnelle (Plan-file) issue du morphisme d'instanciation μₙ [2, 6]. |
| **𝔸ₙ** | `04_FINDINGS.md` & `05_PROGRESS.md` | **Archive gelée** : Réunion des apprentissages (Findings) et des preuves (Progress) [2, 7]. |
| **𝕡ₙ** | **Artefacts / Code** | **Produit** : Livrable concret et versionnable produit pendant le sprint [2, 8]. |
| **𝕄ₙ** | `06_SPRINT_MEMORY.md` | **Sprint Memory** : Recontextualisation minimale (≤ 15 lignes) pour le sprint suivant [2, 9]. |
| **𝕋ᴳ** | `042_𝕋ᴳ_VISION_GLOBALE.md` | **Attracteur Global** : Vision long terme qui maintient le cap du projet [2, 10]. |
| **𝕽** | `00_REFERENTIEL_R.md` | **Référentiel** : Filtre de discipline (3-Strike, 2-Actions) contraignant l'exécution [1, 2]. |
| **𝕍** | `ALGORITHME_DE_SCORING.md` | **Validateur** : Filtre mesurant l'ambiguïté avant d'autoriser l'instanciation [2, 11]. |
| **Δ₀** | `043_Δ₀_CAPTEURS.md` | **Capteurs** : Indicateurs de régime cognitif pour détecter les dérives (rumination, illusion) [2, 12]. |

## Invariants de correspondance
1. **Bijection Backlog/Phases** : 1 item de backlog dans 𝕮ₙ ⇔ 1 phase dans 𝕊ₙ (`task_plan.md`) [13, 14].
2. **Non-Rétroaction** : Les données générées dans `findings.md` ou `progress.md` (𝔸ₙ) ne modifient jamais le contrat en cours (𝕮ₙ) [15, 16].
3. **Vérité Matérielle** : La preuve de complétude d'une phase dans 𝕊ₙ doit correspondre aux critères de la DoD dans 𝕮ₙ [17, 18].
