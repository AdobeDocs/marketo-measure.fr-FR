---
unique-page-id: 18874716
description: Méthodologie de mappage des attributs - [!DNL Marketo Measure]
title: Méthodologie de mappage pour les attributions
exl-id: 4d54dd20-9a82-4b87-8908-ced2bd9c0f2f
feature: Attribution
source-git-commit: cd5597a681f388a5b5c743dadd38bf3127811bff
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 1%

---

# Méthodologie de mappage pour les attributions {#attribution-mapping-methodology}

La méthodologie de mappage des attributs est le processus de recherche de certains objets dans votre gestion de la relation client (contacts, opportunités, comptes) pour créer des points de contact d’attribution dans l’opportunité associée. En d&#39;autres termes, c&#39;est le [!DNL Marketo Measure] une manière de comprendre les points de contact à inclure dans le modèle d’attribution en fonction des processus CRM actuels.

## Mappage des identifiants de compte {#account-id-mapping}

Prêt à l’emploi, [!DNL Marketo Measure] fournit le mappage des ID de compte. Cela signifie que [!DNL Marketo Measure] examine les informations marketing du compte et de ses contacts pour créer des points de contact d’attribution associés à l’opportunité. Vous trouverez ci-dessous une représentation simple de ce processus.

![](assets/1-1.png)

N’oubliez pas que **not all** les points de contact de vos contacts sont transférés vers l’opportunité en tant que points de contact d’attribution. La chronologie de l’opportunité (sa date de première touche - sa date de fermeture) détermine si un point de contact peut influencer l’opportunité. Par conséquent, si un point de contact sur le contact A s’est produit après la perte/la perte de l’opportunité fermée, [!DNL Marketo Measure] ne poussera pas ce point de contact vers l’opportunité. Cette procédure de chronologie est suivie dans tous les autres mappages d’objet d’attribution.

Avantages : Cette méthode d’attribution est très efficace pour la plupart des entreprises. L’équipe marketing n’a pas besoin de compter sur l’équipe commerciale pour associer tous les contacts à une opportunité particulière (ce qui est souvent un problème). De plus, même si une équipe commerciale associe des rôles de contact, de nombreuses interactions de contact avec du matériel marketing peuvent être ignorées. Enfin, cette méthode aide la stratégie ABM qui s&#39;efforce d&#39;influencer la totalité d&#39;un compte, plutôt que des influenceurs spécifiques.

Inconvénients : S’il existe des contrats de niveau de service marketing et de vente forts qui définissent qui doit recevoir le crédit de quoi, cette méthode peut s’avérer problématique. En outre, si les personnes n’utilisent pas les hiérarchies de compte pour définir des entités commerciales spécifiques au sein d’un compte plus important (par exemple : IBM), les interactions marketing spécifiques à une entité commerciale peuvent être réparties sur d’autres opportunités d’entité commerciale.

## Mappage des rôles de contact d’opportunité {#opportunity-contact-role-mapping}

Bien que la plupart des clients utilisent le mappage Identifiant de compte, [!DNL Marketo Measure] Vous pouvez rechercher les rôles de contact (contacts associés à l’opportunité) dans une opportunité pour ventiler le processus d’attribution. Cela signifie que [!DNL Marketo Measure] poussera uniquement les interactions marketing associées aux rôles de contact sur l’opportunité en tant que points de contact d’attribution de l’achat. Vous trouverez ci-dessous une représentation de ce processus.

![](assets/2-1.png)

Avantages : si votre équipe dispose d’un processus de rôles de contact bien défini, ce type de mappage d’attribution peut vous être idéal. Cela permet d’aligner un peu plus les ventes et le marketing, car tout le monde comprendra parfaitement comment l’attribution est ventilée. Ce processus s’avère également utile lorsque les entreprises ciblent plusieurs unités opérationnelles au sein d’une grande entreprise et lorsqu’elles vendent différents produits en même temps.

Inconvénients : Cependant, si aucun processus de rôle de contact n’est en place, le marketing perd de nombreuses données marketing et l’équipe recevra beaucoup moins de crédit pour ses efforts marketing qui influencent les opportunités.

## Mappage des rôles de contact de Principal d’opportunité {#opportunity-primary-contact-role-mapping}

En plus de se contenter d&#39;examiner les rôles de contact sur l&#39;opportunité, [!DNL Marketo Measure] peut se concentrer encore plus sur les contacts de Principal sur une opportunité. Avec cette configuration à l’esprit, [!DNL Marketo Measure] attrape uniquement le point de contact marketing associé aux principaux contacts d’une opportunité et envoie ces informations dans l’histoire d’attribution de cette opportunité spécifique. Voir l’image ci-dessous.

![](assets/3.png)

Avantages : si votre équipe souhaite uniquement comprendre l’influence marketing sur les contacts définis comme &quot;principaux&quot; sur l’opportunité, ce type de mappage convient le mieux à l’équipe.

Inconvénients : C&#39;est certainement le processus de cartographie le moins utilisé et qui peut fortement miner l&#39;influence marketing qui déplace le curseur à travers d&#39;autres contacts sur une opportunité.
