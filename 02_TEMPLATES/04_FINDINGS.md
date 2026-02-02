```
# 𝔸ₙ — Archive Gelée (Apprentissage & Preuve)
**Rôle CPE :** Sortie du morphisme εₙ (Exécution).
**Finalité :** Alimenter τₙ (Distillation) et κₙ (Évolution).
**Condition :** Pas de produit 𝕡ₙ sans archive 𝔸ₙ.
```
Le fichier **findings.md** (noté Fn​) est le réceptacle de la connaissance et de la mémoire technique de votre projet. Dans une exécution manuelle (H=A), il remplit la fonction critique de **"mémoire de travail sur disque"**, empêchant l'évaporation des informations complexes que votre cerveau ne peut pas stocker indéfiniment.

Voici la structure détaillée et les règles de gestion pour ce fichier :

# 1 - Ontologie et Rôle de Fn​

• **Fonction** : Répondre à la question « Qu'ai-je appris ? ».

• **Nature** : Contrairement au plan qui est directif, `findings.md` est **descriptif** et **accumulatif**.

• **Morphisme (f5​)** : Il transforme le contexte d'exécution (recherches, tests) en traces persistantes.
___
# 2 - La Règle d'Or : La "Règle des 2 Actions"

C'est le mécanisme de déclenchement le plus important pour maintenir la cohérence de votre projet.

• **Le principe** : Après avoir effectué **2 actions de lecture** (navigation web, lecture de documentation, visualisation d'images ou de PDF), vous **devez** immédiatement consigner vos découvertes dans `findings.md`.

• **La raison** : Les informations visuelles et multimodales sont les premières à être perdues lors d'un changement de contexte ou d'une interruption.
___

# 3 - Template Détaillé : `findings.md`
Pour garantir la précision et éviter les hallucinations lors des itérations futures, utilisez cette structure :

# Findings & Decisions (Mémoire de Travail)

## 🎯 Requirements & Contraintes
- [Listez ici les besoins spécifiques identifiés lors de la phase de découverte] [8].

## 🔍 Research Findings (Découvertes)
- [Synthèse des informations extraites du web ou des fichiers] [8].
- **Note :** Conservez toujours les URLs et les chemins de fichiers (Pointeurs) même si vous résumez le contenu [14].

## 🛠 Décisions Techniques
| Décision                 | Rationnel (Pourquoi ?)               |
| :----------------------- | :----------------------------------- |
| [Ex: Choix de telle lib] | [Ex: Meilleure performance de cache] |

## ⚠️ Issues & Blocages
| Problème rencontré | Résolution / Piste                      |
| :----------------- | :-------------------------------------- |
| [Erreur X]         | [Fix appliqué ou changement d'approche] |

## 🖼 Observations Visuelles / Browser
- [Notes sur les interfaces testées, captures d'écran décrites en texte] [8].


___

# 4 - Invariants de Gestion pour Fn​

1. **Persistance des erreurs** : Ne supprimez jamais une erreur résolue. Laissez les "mauvais virages" dans le fichier pour que, lors de la prochaine itération, vous ne répétiez pas la même erreur (Principe 5 de Manus).

2. **Compression Restaurable** : Si vous résumez une documentation pour gagner de la place, gardez toujours le lien vers la source complète.

3. **Source de Correction** : Si `findings.md` révèle une impossibilité technique, c'est ce fichier qui force la mise à jour immédiate du `task_plan.md`.
___

# 5 - Analyse : Seuil et Stabilité

• **Stabilité** : Le système est robuste si chaque découverte majeure est liée à une décision documentée.

• **Risque** : Si vous effectuez plus de 5 actions de recherche sans écrire dans `findings.md`, la probabilité de **"dérive de but"** et d'oubli de contraintes critiques augmente de façon exponentielle.

**Analogie** : Considérez `findings.md` comme la **boîte noire** d'un avion. Le `task_plan.md` est le plan de vol, mais la boîte noire enregistre tout ce qui se passe réellement, y compris les turbulences. En cas de problème, c'est en lisant la boîte noire que vous comprenez comment ajuster votre trajectoire pour le reste du voyage.
