---
unique-page-id: 18874684
description: Dates de synchronisation de campagne - [!DNL Marketo Measure]
title: Date de synchronisation de campagne
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
feature: Channels
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 1%

---

# Date de synchronisation de campagne {#campaign-sync-dates}

Découvrez l’impact de la fonction Dates de synchronisation de campagne, ainsi que quelques cas d’utilisation de cette fonctionnalité.

>[!NOTE]
>
>Cet article couvre un processus obsolète. Nous encourageons les utilisateurs à utiliser la variable [nouveau processus in-app amélioré](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

**[!DNL Marketo Measure]Package requis : 6.9 ou version ultérieure**

Cette fonctionnalité se compose de deux champs de date simples sur la variable [!DNL Salesforce] Objet de campagne :

* Date de début du point de contact
* Date de fin du point de contact

Une fois les points de contact d’achat activés sur une campagne spécifique, les dates de synchronisation de campagne vous permettent de définir les paramètres de date de point de contact sur chaque campagne. Ainsi, si vous deviez ajouter une date de fin de point de contact du 1er mars 2017, [!DNL Marketo Measure] crée uniquement des points de contact sur les membres de campagne qui ont été ajoutés à la campagne avant cette date. [!DNL Marketo Measure] ne créera pas de points de contact pour les membres de la campagne qui ont été ajoutés après le 1er mars 2017.

![](assets/1.gif)

De même, si vous deviez ajouter une date de début de point de contact sur une campagne (le 1er janvier 2017, par exemple), [!DNL Marketo Measure] ne créera pas de points de contact sur les membres de campagne qui ont été ajoutés à la campagne avant le 1er janvier 2017. Il n’est pas nécessaire d’ajouter une date de début de point de contact si vous ajoutez une date de fin de point de contact et vice versa.

## Cas d’utilisation {#use-cases}

**Remplissage des points de contact**

Il peut arriver qu’une équipe marketing ne puisse pas ajouter de paramètres utm à un effort marketing particulier. Les dates de synchronisation des campagnes vous permettent de (si vous utilisez des campagnes SFDC pour des efforts en ligne) de renvoyer certaines données manquantes. Supposons que vous exécutiez une campagne par e-mail qui a commencé le 1er mai, mais que votre équipe n’ait pas ajouté de paramètres utm à cette campagne par e-mail avant le 15 mai. Si vous effectuez le suivi des conversions d’emails via une campagne SFDC, vous pourrez définir une date de fin de point de contact le 15 mai sur cette campagne et activer les points de contact pour les membres &quot;réactifs&quot; de la campagne. Cette action indique : [!DNL Marketo Measure] pour créer des points de contact pour toutes ces réponses jusqu’au 15 mai.

**Points de contact de l’adhésion à Campaign rétroactifs**

Si vous êtes nouveau [!DNL Marketo Measure] client, vous pouvez être intéressé par l’introduction de certaines données marketing dont vous avez effectué le suivi via les campagnes SFDC. Cependant, si vous deviez activer les points de contact pour vos campagnes SFDC en ligne, vous pourriez être confronté au problème du double comptage de l’attribution depuis [!DNL Marketo Measure] crée automatiquement des points de contact pour vos efforts de marketing en ligne. Afin d’éviter de comptabiliser deux fois les données, vous pouvez utiliser les dates de fin de point de contact de Campaign pour définir une limite sur les dates de point de contact créées par [!DNL Marketo Measure] sur la campagne de la DDC. Par exemple, si vous souhaitez ajouter des conversions rétroactives pour une campagne Social, vous avez effectué le suivi dans SFDC, mais vous comprenez que vous avez ajouté la variable [!DNL Marketo Measure] JavaScript (qui crée des points de contact en ligne) le 1er juillet, vous pouvez modifier la campagne SFDC Social pour qu’elle contienne une date de fin de point de contact égale au 1er juillet et activer les points de contact d’achat pour cette campagne.

Il peut y avoir de nombreux autres cas d’utilisation pour les dates de fin de point de contact. Si vous avez besoin d&#39;aide pour résoudre une situation spécifique, n&#39;hésitez pas à contacter . [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Université : champs des membres Campaign et Campaign](https://learn.bizible.com/2-bizible-customization/137720https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
