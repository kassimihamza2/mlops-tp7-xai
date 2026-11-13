# Model Card - fraude (version servie par l'alias production)

## Modele

Nom et version dans le registre MLflow : fraude, version 1, alias production.

Famille et reglages : RandomForestClassifier, 500 arbres, profondeur maximale de 16.

Run d'origine (MLflow) : b10467c916ab446387c222fef2e819e0.

## Objectif et usage prevu

Detecter les transactions presentant un risque de fraude afin d'aider les equipes a prioriser les controles humains.

Le modele constitue un outil d'aide a la decision et non un systeme de decision autonome.

## Usages exclus

Ne pas utiliser le modele pour bloquer definitivement un compte ou rejeter automatiquement une transaction sans verification humaine.

Ne pas utiliser sa prediction comme preuve certaine de fraude.

## Donnees

Fichier, nombre de lignes, part de fraudes, empreinte : data/transactions.csv, 5 000 transactions, 568 fraudes (11,36 %), MD5 : cf9f6f86c141e7df32c61715c493483f.

Origine des donnees : donnees synthetiques utilisees dans le cadre du TP.

## Performances (jeu de test, 1 250 transactions)

F1 : 0.8669.

Precision : 0.8837.

Rappel : 0.8507.

AUC : 0.9872.

## Methodes d'explicabilite

Globale : importance par permutation et SHAP TreeExplainer sur 400 transactions.

Locale : SHAP et LIME, notamment pour la transaction de Mme Benali.

Variables influentes : montant, frequence sur 24 heures, anciennete et execution de nuit. LIME montre une variabilite selon la graine, notamment pour freq_24h.

## Comparaison avec un modele interpretable

La regression logistique avec log10(montant) atteint un F1 de 0.8593 et detecte 113 fraudes sur 134, contre 0.8669 et 114 fraudes pour la foret.

L'arbre de profondeur 3 est plus lisible, mais atteint un F1 de 0.5737 et detecte 72 fraudes sur 134.

## Limites et risques connus

Les donnees ne garantissent pas des performances identiques sur des transactions reelles. Les cas rares et les changements de comportement peuvent degrader les resultats.

SHAP decrit les contributions du modele sans etablir de causalite. Les explications LIME peuvent varier selon les parametres et la graine aleatoire.

## Recommandations d'utilisation et de surveillance

Faire verifier les alertes par un analyste avant toute decision importante. Surveiller regulierement les performances, le rappel et les faux positifs.

Reevaluer le modele en cas de changement du comportement des transactions ou de baisse des performances.

## Tracabilite

Run des explications (experience tp7-explicabilite) : 730853bd965e4393a87a8fdef8d029a7.

Auteurs : Hamza Kassimi.

Date : 13/11/2026.

Prochaine revue : 13/02/2027.

