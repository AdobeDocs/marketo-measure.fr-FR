---
unique-page-id: 18874716
description: Méthodologie de mappage des attributs - [!DNL Marketo Measure] - Documentation du produit
title: Méthodologie de mappage des attributs
exl-id: 4d54dd20-9a82-4b87-8908-ced2bd9c0f2f
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# Méthodologie de mappage des attributs {#attribution-mapping-methodology}

La méthodologie de mappage des attributs est le processus de recherche de certains objets dans votre gestion de la relation client (contacts, opportunités, comptes) pour créer des points de contact d’attribution dans l’opportunité associée. En d&#39;autres termes, c&#39;est le [!DNL Marketo Measure] une manière de comprendre les points de contact à inclure dans le modèle d’attribution en fonction des processus CRM actuels.

## Mappage des identifiants de compte {#account-id-mapping}

Prêt à l’emploi, [!DNL Marketo Measure] fournit le mappage des ID de compte. Cela signifie que [!DNL Marketo Measure] examine les informations marketing du compte et de ses contacts pour créer des points de contact d’attribution associés à l’opportunité. Vous trouverez ci-dessous une représentation simple de ce processus.

![](assets/1-1.png)

Gardez à l’esprit que **not all** les points de contact de vos contacts seront transférés dans l’opportunité en tant que points de contact d’attribution. La chronologie de l’opportunité (date de première touche - date fermée) détermine si un point de contact peut influencer l’opportunité. Par conséquent, si un point de contact sur le contact A s’est produit après la perte/la perte de l’opportunité fermée, [!DNL Marketo Measure] ne poussera pas ce point de contact vers l’opportunité. Cette procédure de chronologie est suivie sur tous les autres mappages d’objet d’attribution.

Avantages : Cette méthode d’attribution est très efficace pour la plupart des entreprises. L’équipe marketing n’a pas besoin de compter sur l’équipe commerciale pour associer tous les contacts à une opportunité particulière (ce qui est souvent un problème). De plus, même si une équipe commerciale associe des rôles de contact, de nombreuses autres interactions de contact avec du matériel marketing peuvent être ignorées. Enfin, cette méthode aide les stratégies ABM qui s&#39;efforcent d&#39;influencer la totalité d&#39;un compte, plutôt que des influenceurs spécifiques.

Inconvénients : S’il existe des contrats de niveau de service marketing et de vente forts qui définissent qui doit obtenir du crédit pour quoi, cette méthode peut s’avérer problématique. En outre, si les personnes n’utilisent pas les hiérarchies de compte pour définir des entités commerciales spécifiques dans un compte plus grand (par exemple : IBM), les interactions marketing spécifiques à une unité opérationnelle peuvent ensuite être réparties entre d’autres opportunités d’unité opérationnelle.

## Mappage des rôles de contact d’opportunité {#opportunity-contact-role-mapping}

Bien que la plupart des clients exploitent le mappage des ID de compte, [!DNL Marketo Measure] a la possibilité de rechercher les rôles de contact (contacts associés à l’opportunité) dans une opportunité pour ventiler le processus d’attribution. Cela signifie que [!DNL Marketo Measure] poussera uniquement les interactions marketing associées aux rôles de contact sur l’opportunité en tant que points de contact d’attribution de l’achat. Vous trouverez ci-dessous une représentation de ce processus.

![](assets/2-1.png)

Avantages : Si votre équipe dispose d’un processus de rôles de contact très bien défini, ce type de mappage d’attribution peut s’avérer idéal pour vous. Cela permettra d’aligner un peu plus les ventes et le marketing, car tout le monde comprendra parfaitement comment l’attribution est ventilée. Ce processus s’avère également très utile lorsque les entreprises ciblent plusieurs unités commerciales au sein d’une grande entreprise, ainsi que lorsqu’elles vendent différents produits en même temps.

Inconvénients : Cependant, s’il n’existe aucun processus de rôle de contact en place, le marketing perdra de nombreuses données marketing et l’équipe recevra beaucoup moins de crédit pour ses efforts marketing qui influencent les opportunités.

## Mappage des rôles de contact Principal opportunité {#opportunity-primary-contact-role-mapping}

En plus de se contenter d&#39;examiner les rôles de contact sur l&#39;opportunité, [!DNL Marketo Measure] peut se concentrer encore plus sur les contacts Principal d&#39;une opportunité. Avec cette configuration à l’esprit, [!DNL Marketo Measure] ne saisira que le point de contact marketing associé aux Principaux contacts d’une opportunité et poussera ces informations dans l’histoire d’attribution de cette opportunité spécifique. Voir l’image ci-dessous.

![](assets/3.png)

Avantages : Si votre équipe souhaite uniquement comprendre l’influence marketing exercée sur les contacts définis comme &quot;Principaux&quot; sur l’opportunité, ce type de mappage sera adapté le mieux à l’équipe.

Inconvénients : C&#39;est certainement le processus de cartographie le moins utilisé et qui peut fortement miner l&#39;influence marketing qui déplace le curseur à travers d&#39;autres contacts sur une opportunité.
