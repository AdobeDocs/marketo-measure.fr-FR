---
description: Maintenance des [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Maintenance de [!DNL Marketo Measure]
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 95%

---


# Maintenance de [!DNL Marketo Measure] {#marketo-measure-maintenance}

[!DNL Marketo Measure] extrait presque tout ce dont il a besoin de votre CRM au quotidien, mais il reste quelques tâches de maintenance que vous devez planifier régulièrement pour que [!DNL Marketo Measure] continue à fonctionner et à produire les informations les plus précises possible.

**Synchroniser les Buyer Touchpoints pour les nouvelles campagnes hors ligne (2 fois par mois)**

Comme vous l’avez appris lors de l’intégration, [!DNL Marketo Measure] obtient des informations sur vos efforts marketing hors ligne en se synchronisant avec les campagnes de votre CRM. Lorsque votre organisation lance de nouvelles campagnes, veillez à activer Buyer Touchpoints pour chaque campagne, le cas échéant.

**Charger les dépenses pour tous les canaux (1 fois par mois)**

Pour bénéficier de toutes les fonctionnalités de reporting des revenus et du retour sur investissement dans [!DNL Marketo Measure], vous devez indiquer à [!DNL Marketo Measure] combien vous dépensez pour chacun de vos canaux et sous-canaux de marketing. Désignez la personne propriétaire de chaque canal/sous-canal et demandez à ces personnes de rendre compte des dépenses à une seule partie responsable du chargement des nouvelles informations sur les coûts une fois par mois.

Pour un rappel sur la façon de charger des informations sur les coûts, lisez [cet article](/help/marketing-channel-costs.md).

**Mettre à jour la liste des domaines à suivre (1 fois par mois)**

Marketo Measure suit toutes les pages et tous les sous-domaines dans lesquels notre code Javascript est actif, mais seulement pour les domaines que nous connaissons. Si vous avez récemment débogué un nouveau domaine, étendu à l&#39;international ou modifié votre domaine principal, contactez l&#39;assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour vous assurer que nous mettons à jour votre compte en conséquence.

**Vérifier l’exactitude du mappage des canaux personnalisés (1 fois par mois)**

Lors de l’intégration, vous établissez un mappage personnalisé des canaux pour vos efforts marketing en ligne et hors ligne. Au fur et à mesure que votre stratégie marketing et votre utilisation de Marketo Measure évoluent, vous devez garder un œil sur cette logique de mappage pour vous assurer que tous vos points de contact sont catégorisés comme il se doit.

N’oubliez pas que [!DNL Marketo Measure] retraite vos données lorsque vous modifiez la logique de mappage. Vous ne pourrez donc pas modifier ces règles plus d’une fois tous les sept jours.

Consultez [cet article](/help/channel-tracking-and-setup/online-custom-channel-setup.md) pour la configuration en ligne, [cet article](/help/channel-tracking-and-setup/offline-custom-channel-setup.md) pour la configuration hors ligne, et cette liste de bonnes pratiques établie par nos clientes et clients :

* Examinez les points de contact qui relèvent actuellement des canaux « Autres » ou « NULL » que vous pourriez avoir mis en place. Le cas échéant, mettez à jour votre logique de mappage pour recatégoriser ces points de contact dans des canaux plus précis.
* Examinez les points de contact qui relèvent actuellement de vos canaux directs. Si certaines de vos campagnes marketing par e-mail ou certains de vos autres efforts ne disposent pas de certains paramètres UTM, il y a de fortes chances que le trafic soit regroupé de manière inappropriée dans un canal direct. Pensez à mettre à jour vos paramètres UTM pour capturer la source de référence.

**Évaluer les paramètres de suppression des points de contact (1 fois par trimestre)**

S’il existe de nombreux points de contact dont vous préféreriez qu’ils ne soient pas pris en compte dans votre story d’attribution (à partir d’un [!DNL Login] ou de [!DNL Unsubscribe forms], d’une page Carrières ou d’une application interne, par exemple), il peut être conseillé d’évaluer vos paramètres de suppression des points de contact existants. Une fois par trimestre, identifiez les groupes de points de contact qui créent un bruit inutile et mettez à jour votre logique de suppression en conséquence. [Voici un article utile](/help/channel-tracking-and-setup/touchpoint-removal-and-touchpoint-suppression.md) qui explique comment procéder.

**Vérifier l’exactitude du mappage des étapes personnalisées (1 fois par trimestre) (le cas échéant)**

Si vous utilisez des étapes personnalisées [!UICONTROL Prospect], [!UICONTROL Contact], ou [!UICONTROL Opportunités], vous pouvez également avoir personnalisé la partie du pipeline à laquelle ces étapes correspondent et si ces étapes sont incluses dans un modèle d’attribution personnalisé. Une fois par trimestre, consultez [cet article](/help/channel-tracking-and-setup/custom-attribution-model-and-setup.md) pour vous rappeler comment réaliser le mappage des étapes personnalisées et vous assurer que vous suivez avec précision vos étapes personnalisées.

**Comparer le modèle de machine learning à la pondération du modèle personnalisé (1 fois par trimestre) (le cas échéant)**

Si vous disposez d’une licence pour le modèle personnalisé [!DNL Marketo Measure], vous avez également accès aux données de notre modèle de machine learning (MLM) dans [!UICONTROL Paramètres] > [!UICONTROL Paramètres d’attribution]. Le MLM calcule l’importance de chaque étape à l’aide des données des points de contact de votre compte et peut vous aider à décider comment allouer le poids d’attribution dans votre modèle personnalisé. Nous vous recommandons de comparer le MLM à votre modèle personnalisé une fois par trimestre et de discuter des implications de possibles changements de votre modèle personnalisé avec la personne chargée de la gestion de votre portefeuille.

Pour plus d’informations sur le modèle de machine learning [!DNL Marketo Measure], consultez [cet article](/help/channel-tracking-and-setup/machine-learning-model-faq.md).
