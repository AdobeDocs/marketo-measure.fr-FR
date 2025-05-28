---
unique-page-id: 18874716
description: Méthodologie de mappage d’attribution - [!DNL Marketo Measure]
title: Méthodologie de mappage pour les attributions
exl-id: 4d54dd20-9a82-4b87-8908-ced2bd9c0f2f
feature: Attribution
source-git-commit: 90d0d6481e5b338d08a56f555ca3addea8bdd304
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Méthodologie de mappage pour les attributions {#attribution-mapping-methodology}

La méthodologie de mappage d’attribution est le processus de recherche de certains objets dans votre CRM (contacts, opportunités, comptes) pour créer des points de contact d’attribution dans l’opportunité associée. En d’autres termes, il s’agit du [!DNL Marketo Measure] moyen de comprendre les points de contact à inclure dans le modèle d’attribution en fonction des processus de votre CRM actuel.

## Mappage de l’ID de compte {#account-id-mapping}

Par défaut, [!DNL Marketo Measure] fournit le mappage des identifiants de compte. Cela signifie que [!DNL Marketo Measure] examine le compte et ses informations marketing Contacts pour créer des points de contact d’attribution associés à l’opportunité. Vous trouverez ci-dessous une simple représentation de ce processus.

![](assets/1-1.png)

Gardez à l’esprit que **tous** points de contact de vos contacts ne sont pas intégrés dans l’opportunité en tant que points de contact d’attribution. La chronologie de l’opportunité (sa date de premier contact - date de fermeture) détermine si un point de contact compte comme influenceur sur l’opportunité. Par conséquent, si un point de contact sur le contact A s’est produit après la fermeture de l’opportunité (confirmée/perdue), [!DNL Marketo Measure] ne poussera pas ce point de contact vers l’opportunité. Cette procédure de chronologie est suivie pour tous les autres mappages d’objet d’attribution.

Avantages : Cette méthode d’attribution est très efficace pour la plupart des entreprises. L&#39;équipe marketing n&#39;a pas besoin de compter sur l&#39;équipe des ventes pour associer tous les contacts à une opportunité particulière (ce qui est souvent un problème). De plus, même si une équipe de vente associe des rôles de contact, il se peut que de nombreuses autres interactions du contact avec les documents marketing ne soient pas prises en compte. Enfin, cette méthode aide la stratégie ABM qui vise à influencer l&#39;ensemble d&#39;un compte, plutôt que des influenceurs spécifiques.

Inconvénients : s’il existe des contrats de niveau de service marketing et vente solides qui définissent qui doit obtenir du crédit pour quoi, cette méthode peut s’avérer problématique. En outre, si les utilisateurs n’utilisent pas les hiérarchies de comptes pour définir des unités opérationnelles spécifiques dans un compte plus grand (par exemple, IBM), les interactions marketing spécifiques à une unité opérationnelle peuvent être réparties entre d’autres opportunités d’unité opérationnelle.

## Mappage du rôle du contact de l’opportunité {#opportunity-contact-role-mapping}

>[!NOTE]
>
>Les méthodes de mappage des rôles de contact ne sont disponibles que pour ceux qui utilisent Salesforce comme CRM. Il n’est pas disponible pour les utilisateurs et utilisatrices de Microsoft Dynamics en raison de l’absence d’objet de rôle de contact dans ce CRM.

Bien que la plupart des clients utilisent le mappage des identifiants de compte, [!DNL Marketo Measure] pouvez rechercher des rôles de contact (contacts associés à l’opportunité) dans une opportunité pour ventiler le processus d’attribution. Cela signifie que [!DNL Marketo Measure] intégrerez uniquement les interactions marketing associées aux rôles de contact sur l’opportunité en tant que points de contact d’attribution de l’acheteur. Vous trouverez ci-dessous une représentation de ce processus.

![](assets/2-1.png)

Avantages : si votre équipe dispose d’un processus de rôles de contact bien défini, ce type de mappage d’attribution peut être idéal pour vous. Cela permet d’aligner un peu plus les ventes et le marketing, car tout le monde comprend parfaitement comment l’attribution est décomposée. Ce processus s’avère également utile lorsque les organisations ciblent plusieurs unités opérationnelles au sein d’une grande entreprise et lorsqu’elles vendent différents produits en même temps.

Inconvénients : Cependant, si aucun processus de rôle de contact n’est en place, le marketing perd beaucoup de données marketing et l’équipe finit par recevoir beaucoup moins de crédit pour ses efforts de marketing qui influencent les opportunités.

## Mappage du rôle du contact du Principal d’opportunité {#opportunity-primary-contact-role-mapping}

Au-delà du simple examen des rôles de contact sur l’opportunité, [!DNL Marketo Measure] pouvez vous concentrer encore plus pour n’examiner que les contacts de Principal sur une opportunité. Avec cette configuration à l’esprit, [!DNL Marketo Measure] ne récupère que le point de contact marketing associé aux contacts principaux sur une opportunité et transmet ces informations dans l’histoire d’attribution de cette opportunité spécifique. Voir l’image ci-dessous.

![](assets/3.png)

Avantages : si votre équipe souhaite uniquement comprendre l’influence marketing sur les contacts définis comme « principaux » pour l’opportunité, ce type de mappage convient le mieux à l’équipe.

Inconvénients : Il s&#39;agit certainement du processus de cartographie le moins utilisé et il peut fortement saper l&#39;influence marketing qui fait bouger l&#39;aiguille dans d&#39;autres contacts sur une opportunité.
