---
unique-page-id: 27656441
description: FAQ sur l’intégration de la dérive - [!DNL Marketo Measure]
title: Questions fréquentes sur l’intégration de Drift
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
feature: Integration
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 2%

---

# Questions fréquentes sur l’intégration de Drift {#drift-integration-faq}

Dans le cadre de la [!DNL Marketo Measure] intégration à Drift, voici quelques-unes des questions les plus fréquemment posées. Si aucune question n’est décrite ci-dessous, contactez l’équipe du compte Adobe (votre gestionnaire de compte) ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

**Comment l’intégration est-elle activée ?**

Suivi de la conversation de dérive pour [!DNL Marketo Measure] est activé par défaut. Si vous souhaitez le désactiver (et ne pas créer de points de contact à partir des conversations de dérive par défaut), ajoutez un attribut supplémentaire à votre [!DNL Marketo Measure] Mise en oeuvre de JavaScript, en gras ci-dessous :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

Pour ceux qui utilisent [!DNL Google Tag Manager] pour charger la variable [!DNL Marketo Measure] Si vous souhaitez exclure vos conversations au débit de l’option Point de contact, ajoutez à ce qui suit : `<span>` juste après votre [!DNL Marketo Measure] Script :

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**Que fait l’intégration ?**

L’intégration permet désormais [!DNL Marketo Measure] pour savoir quand un utilisateur final fournit son adresse électronique dans une conversation Drift. De là, nous créons des points de contact à partir de ces interactions avec un type de point de contact &quot;Conversation Web&quot;. Cette intégration permet aux marketeurs de comprendre les performances de leurs interactions de discussion, ainsi que les canaux, sous-canaux et campagnes qui incitent les internautes à interagir avec ces conversations.

**Que se passe-t-il si je suis la dérive via des règles de synchronisation de campagne ?**

Si des règles de synchronisation de campagne sont en place pour créer des points de contact pour les interactions de conversation de dérive, veillez à cesser d’ajouter ces utilisateurs finaux spécifiques à la campagne CRM correspondante. Sinon, une fois que le bit de fonctionnalité est activé, créez un point de contact CRM Campaign et un point de contact numérique pour une interaction de conversation de dérive.

**Que se passe-t-il si je suis la dérive via les campagnes CRM ?**

Si des campagnes CRM sont en place pour créer des points de contact pour les interactions de conversation en direct, une Date de fin de point de contact doit être définie sur ces campagnes spécifiques (la Date de fin du point de contact doit être la date à laquelle le bit de la fonction d’intégration de la conversation Web est activé).

**Que se passe-t-il si je suis la dérive via les activités ?**

Si des règles d’activité sont en place pour créer des points de contact pour les interactions de conversation de dérive, une logique supplémentaire doit être ajoutée aux règles. Ajoutez une logique à l’aide du champ Date de création de la tâche pour empêcher la duplication des points de contact (IE CrmTask.CreatedDate est Inférieur à la date à laquelle le bit de fonction a été activé). Voir la capture d’écran ci-dessous, par exemple.

![](assets/activity-rule-drift.png)
