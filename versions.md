---
layout: default
title: "Versions"
---

# Page dédiée à la description des différentes versions de la stratégie et à l’évolution des réflexions

# Version 0 (idée de base)

Analyser les news pour repérer les mauvaises nouvelles liées aux entreprises et short les actions d’entreprises subissant des coups durs.

# Version 0.1

La version 0 est très ambitieuse, il faut traiter un trop grand nombre de données. 

Pour le moment, on va se focaliser sur un seul type d’évènement qui arrive régulièrement chez toutes les entreprises et qui provoque des mouvements du prix de leurs actions → *La publication des résultats*

Pour ce faire : 

- On scrappe les calendriers des sites comme ZoneBourse.
- On scrappe les prévisions analystes sur ces mêmes sites.
- On scrappe les résultats de l’entreprise ciblée une fois publiés.
- On demande à un LLM de comparer les prévisions et les résultats afin de prédire si le cours de l’action va monter ou descendre.

# Version 0.2 (actuelle)

Dans la version 0.1, on scrappe les données dont on a besoin, ce qui est source d’erreur et peu fiable, et qu'on ne peut pas mettre en production.

De plus, beaucoup des informations sur les prédictions des analystes sont très difficiles à trouver. Il faut scrapper des sites spécialisés ou s’abonner à des bases de données financières hors budget.

Cette version utilise PerplexityAI, un outil IA payant qui permet de faire des recherches sur Internet par un LLM pour trouver de manière fiable les informations nécessaires en scrappant seul les meilleurs sites.

# Version 0.3 (coming)

Refonte de tous les prompts → [Prompts](https://www.notion.so/b24e406208b340bfa861f2d68d20e905?pvs=21). Au fil des utilisations, je me suis rendu compte que beaucoup d’informations retrouvées étaient erronées. C’est probablement dû au fait qu’on en demande beaucoup en un seul prompt et que le LLM s’y perd. Je vais donc diviser nos requêtes en plusieurs prompts plus courts, simplifiant la tâche pour le LLM. Cela ne va pas augmenter les coûts d’API car on paye par token (entrée/sortie), pas par requête.

J’ai aussi revu nos priorités dans les informations financières à retrouver dans le earnings report → [Comparer un rapport financier et les prévisions analystes](https://www.notion.so/Comparer-un-rapport-financier-et-les-pr-visions-analystes-491cad35408a41edb8993f7f095b05ad?pvs=21).

L’architecture entière du code a été repensée : désormais, les fonctions complexes et longues sont dans des classes appelées *manager*, pour que le code soit modulaire, facilement maintenable et compréhensible par tous les membres de l’équipe.

La pipeline est testable dans le notebook `pipeline.ipynb`.
