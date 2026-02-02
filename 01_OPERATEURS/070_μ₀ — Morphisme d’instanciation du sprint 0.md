[IDENTITÉ]  
μ₀ — Morphisme d’instanciation du sprint 0  
  
[FINALITÉ]  
Transformer un contrat validé et un contexte en un sprint exécutable.  
Fixer ce qui doit être fait et ce qui ne doit pas l’être.  
  
[ENTRÉES] :

    ◦ C0​ (contrat)

    ◦ M−1​,p−1​ (initialement vides)

    ◦ TG **(attracteur global)**

    ◦ T0​ (attracteur local)

    ◦ Δ0​ **(capteurs)**

    ◦ **Condition :** ∣R **(sous filtre du référentiel)**
  
[SORTIES]  
– 𝕊₀ (sprint instancié)  
  
[INVARIANTS]  
– Ne modifie pas le contrat  
– Ne produit aucun livrable  
– Fige le périmètre du sprint  
  
[RÈGLES D’ACTIVATION]  
– Uniquement après validation du contrat  
– Bloqué si 𝕋₀ est absent  
  
[ANTI-PATHOLOGIES]  
– Sprint flou  
– Travail hors périmètre  
– Confusion entre préparation et exécution  
  
[POSITION DANS LA CHAÎNE]  
x = 5
