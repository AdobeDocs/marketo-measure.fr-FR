---
description: Conseils sur les FAQ relatives à l’intégration de Drift pour les utilisateurs de Marketo Measure
title: Questions fréquentes sur l’intégration de Drift
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
feature: Integration
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 1%

---

# Questions fréquentes sur l’intégration de Drift {#drift-integration-faq}

Dans le cadre de l’intégration [!DNL Marketo Measure] à Drift, voici quelques-unes des questions les plus fréquemment posées. Pour toute question non décrite ci-dessous, contactez l’équipe du compte Adobe (votre gestionnaire de compte) ou l’assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

**Comment l’intégration est-elle activée ?**

Le suivi des conversations à la dérive pour [!DNL Marketo Measure] est activé par défaut. Si vous souhaitez la désactiver (et ne pas créer de points de contact à partir des conversations en direct par défaut), ajoutez un attribut supplémentaire ajouté à votre implémentation JavaScript [!DNL Marketo Measure], en gras ci-dessous :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

Pour ceux qui utilisent [!DNL Google Tag Manager] pour charger le script [!DNL Marketo Measure], si vous souhaitez exclure vos conversations glissantes de l’éligibilité au point de contact, ajoutez les `<span>` suivantes juste après votre script [!DNL Marketo Measure] :

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**À quoi sert l’intégration ?**

L’intégration [!DNL Marketo Measure] permet désormais de savoir quand un utilisateur final fournit son adresse e-mail dans un chat Drift. À partir de là, nous créons des points de contact à partir de ces interactions avec un Type de point de contact de « conversation web ». Cette intégration permet aux professionnels du marketing de comprendre les performances de leurs interactions de conversation, ainsi que les canaux/sous-canaux/campagnes qui poussent les personnes à interagir avec ces conversations.

**Que se passe-t-il si j’effectue le suivi de la dérive via des règles de synchronisation de campagne ?**

Si des règles de synchronisation de campagne sont en place pour créer des points de contact pour les interactions de chat Drift, assurez-vous de cesser d’ajouter ces utilisateurs finaux spécifiques dans la campagne CRM correspondante. Sinon, une fois le bit de fonctionnalité activé, créez un point de contact CRM Campaign et un point de contact numérique pour une interaction de conversation sur Drift.

**Que faire si je suis la dérive via des campagnes CRM ?**

Si des campagnes CRM sont en place pour créer des points de contact pour les interactions de conversation, une date de fin de point de contact doit être définie pour ces campagnes spécifiques (la date de fin de point de contact doit être la date à laquelle la fonctionnalité Intégration de conversation web est activée).

**Que faire si je suis la dérive via les activités ?**

Si des règles d’activité sont en place pour créer des points de contact pour les interactions de conversation, un élément logique supplémentaire doit être ajouté aux règles. Ajoutez une logique à l’aide du champ Date de création de tâche pour empêcher la duplication des points de contact d’être créés (IE CrmTask.CreatedDate est inférieure à la date à laquelle le bit de fonctionnalité a été activé). Voir la capture d’écran ci-dessous par exemple.

![Si des règles d’activité sont en place pour créer des points de contact pour la dérive](assets/chat-integration-1.png)
