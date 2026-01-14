---
description: Instructions de dates de synchronisation de la campagne pour les utilisateurs de Marketo Measure
title: Dates de synchronisation de campagne
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 4%

---

# Dates de synchronisation de campagne {#campaign-sync-dates}

Découvrez la fonction Dates de synchronisation de la campagne et proposez des cas d’utilisation pour cette fonctionnalité.

>[!NOTE]
>
>Cet article traite d’un processus obsolète. Nous encourageons les utilisateurs et les utilisatrices à utiliser le [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/custom-campaign-sync.md){target="_blank"}.

Package **[!DNL Marketo Measure]requis : 6.9 ou version ultérieure**

Cette fonctionnalité se compose de deux champs de date simples sur l’objet [!DNL Salesforce] Campaign :

* Date de début du point de contact
* Date de fin du point de contact

Une fois que les points de contact des acheteurs sont activés sur une campagne particulière, les dates de synchronisation de la campagne vous permettent de définir les paramètres de date des points de contact sur la campagne individuelle. Ainsi, si vous deviez ajouter une date de fin de point de contact fixée au 1er mars 2017, [!DNL Marketo Measure] ne créerez que des points de contact sur les membres de la campagne qui ont été ajoutés à la campagne avant cette date. [!DNL Marketo Measure] ne créera pas de points de contact pour les membres de la campagne qui ont été ajoutés après le 1er mars 2017.

![Une fois que les points de contact de l’acheteur sont activés sur une campagne particulière, les dates de synchronisation de la campagne](assets/legacy-processes-3.gif)

De même, si vous deviez ajouter une Date de début de point de contact sur une campagne (disons le 1er janvier 2017), [!DNL Marketo Measure] ne créerez pas de points de contact sur les membres de la campagne qui ont été ajoutés avant le 1er janvier 2017. Vous n’avez pas besoin d’ajouter de date de début de point de contact si vous ajoutez une date de fin de point de contact et vice versa.

## Cas d’utilisation {#use-cases}

**Remplissage des points de contact**

Il peut arriver qu’une équipe marketing ne parvienne pas à ajouter les paramètres utm à un effort marketing particulier. Les dates de synchronisation de la campagne vous permettent (si vous utilisez des campagnes SFDC pour des efforts en ligne) de renvoyer certaines données manquantes. Supposons que vous exécutiez une campagne par e-mail qui a débuté le 1er mai, mais que votre équipe n’ait pas ajouté de paramètres utm à cette campagne par e-mail avant le 15 mai. Si vous effectuez le suivi des conversions d’e-mails via une campagne SFDC, vous pourrez définir une date de fin de point de contact fixée au 15 mai pour cette campagne et activer les points de contact pour les membres « ayant répondu » de la campagne. Cette action [!DNL Marketo Measure] indiquera de créer des points de contact pour toutes ces réponses jusqu’au 15 mai.

**Points de contact d’appartenance rétroactive à une campagne**

Si vous êtes un nouveau client [!DNL Marketo Measure], il se peut que vous souhaitiez apporter certaines des données marketing que vous avez suivies via les campagnes SFDC. Cependant, si vous deviez activer les points de contact pour vos campagnes SFDC en ligne, vous pourriez rencontrer le problème du double comptage de l’attribution, car [!DNL Marketo Measure] crée automatiquement des points de contact pour vos efforts de marketing en ligne. Afin d’éviter de doubler le comptage des données, vous pouvez utiliser les dates de fin des points de contact de la campagne pour définir une limite des dates des points de contact créées par [!DNL Marketo Measure] dans la campagne SFDC. À titre d’exemple, si vous souhaitez ajouter des conversions rétroactives pour une campagne sur les réseaux sociaux que vous avez suivie dans SFDC, mais que vous comprenez que vous avez ajouté le [!DNL Marketo Measure] JavaScript (qui crée des points de contact en ligne) le 1er juillet, vous pouvez modifier la campagne sur les réseaux sociaux SFDC afin qu’elle contienne une date de fin de point de contact égale au 1er juillet et activer les points de contact acheteur pour cette campagne.

Il peut y avoir de nombreux autres cas d’utilisation pour les dates de fin de point de contact. Si vous avez besoin d&#39;aide pour comprendre une situation spécifique, n&#39;hésitez pas à contacter l&#39;assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
