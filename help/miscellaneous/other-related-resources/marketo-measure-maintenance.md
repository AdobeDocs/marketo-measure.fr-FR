---
unique-page-id: 18874556
description: "[!DNL Marketo Measure] Maintenance - [!DNL Marketo Measure] - Documentation du produit"
title: "[!DNL Marketo Measure] Maintenance"
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# [!DNL Marketo Measure] Maintenance {#marketo-measure-maintenance}

[!DNL Marketo Measure] récupère presque tous les besoins de votre CRM tous les jours, mais vous devrez planifier régulièrement quelques tâches de maintenance pour conserver [!DNL Marketo Measure] avec des informations très précises.

**Synchroniser les points de contact des acheteurs pour les nouvelles campagnes hors ligne (2x/mois)**

Comme vous l&#39;avez appris lors de l&#39;intégration : [!DNL Marketo Measure] obtient des informations sur vos efforts de marketing hors ligne en synchronisant avec les campagnes de la gestion de la relation client. Lorsque votre entreprise lance de nouvelles campagnes, veillez à activer les points de contact d’achat pour chaque campagne, le cas échéant. Consulter [cet article](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)pour plus d’informations.

**Dépense de chargement pour tous les canaux (1x/mois)**

Pour tirer parti des fonctionnalités de création de rapports de retour sur investissement et de chiffre d’affaires complètes d’[!DNL Marketo Measure], vous devez indiquer [!DNL Marketo Measure] combien vous dépensez pour chacun de vos canaux et sous-canaux marketing ? Nous vous recommandons de désigner le propriétaire de chaque canal/sous-canal et de demander à ces personnes de signaler les dépenses à une seule partie responsable du transfert des nouvelles informations de coût sur une base mensuelle.

Actualisez votre mémoire pour savoir comment télécharger des informations de coût en lisant [cet article](/help/marketing-spend/spend-management/marketing-channel-costs.md).

**Mise à jour de la liste des domaines à suivre (1x/mois)**

Marketo Measure effectue le suivi de toutes les pages et sous-domaines pour lesquels notre JavaScript est principal, mais uniquement pour les domaines que nous connaissons. Si vous avez récemment débogué un nouveau domaine, développé à l’international ou modifié votre Principal domaine, contactez [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour vous assurer que nous mettons à jour votre compte en conséquence.

**Vérification du mapping de canal personnalisé pour plus de précision (1x/mois)**

Lors de l’intégration, vous configurez un mappage personnalisé pour vos efforts de marketing en ligne et hors ligne. Au fur et à mesure de l’évolution de votre stratégie marketing et de votre utilisation de Marketo Measure, vous souhaiterez garder un oeil sur cette logique de mappage pour vous assurer que tous vos points de contact sont correctement catégorisés.

Souvenez-vous, [!DNL Marketo Measure] retraite vos données lorsque vous modifiez la logique de mappage, de sorte que vous ne pourrez pas modifier ces règles plus d’une fois tous les 7 jours.

Référence [cet article](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) pour la configuration en ligne, [cet article](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) pour la configuration hors ligne, et cette liste des bonnes pratiques traitées par nos clients :

* Examinez les points de contact qui tombent actuellement dans n’importe quel canal &quot;Autre&quot; ou &quot;NULL&quot; que vous avez configuré. Le cas échéant, mettez à jour votre logique de mappage pour reclasser ces points de contact dans des canaux plus précis.
* Examinez les points de contact qui tombent actuellement dans vos canaux directs. Si des paramètres UTM sont absents de certaines de vos campagnes de marketing par e-mail ou d’autres efforts, il est fort possible que le trafic soit incorrectement regroupé dans un canal Direct. Envisagez de mettre à jour vos paramètres UTM pour capturer la source de référence.

**Évaluation des paramètres de suppression des points de contact (1x/trimestre)**

Si vous constatez de nombreux points de contact que vous préféreriez ne pas prendre en compte dans votre article d’attribution (d’un [!DNL Login] ou [!DNL Unsubscribe forms], une page Carrières ou une application interne, par exemple), vous pouvez évaluer vos paramètres de suppression de point de contact existants. Une fois par trimestre, identifiez tous les groupes de points de contact qui créent des bruits inutiles et mettez à jour votre logique de suppression de manière appropriée. [Voici un article utile :](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)  avec le mode d’emploi.

**Vérification du mappage des étapes personnalisé pour plus de précision (1x/trimestre) (le cas échéant)**

Si vous utilisez des [!UICONTROL prospect], [!UICONTROL Contact]ou [!UICONTROL Opportunités] étapes, vous avez peut-être également personnalisé la partie du pipeline vers laquelle ces étapes sont mappées et si ces étapes sont incluses ou non dans un modèle d’attribution personnalisé. Une fois par trimestre, visite [cet article](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md) pour actualiser votre mémoire lors d’un mappage intermédiaire personnalisé et vous assurer que vous effectuez le suivi précis de vos scènes personnalisées.

**Comparer le modèle d’apprentissage automatique à la pondération de modèle personnalisé (1x/trimestre) (le cas échéant)**

Si vous possédez une licence pour la variable [!DNL Marketo Measure] Modèle personnalisé, vous disposez également de données provenant de notre modèle d’apprentissage automatique (MLM) dans [!UICONTROL Paramètres] > [!UICONTROL Paramètres d’attribution]. Le MLM calcule l’importance de chaque étape à l’aide des données de point de contact de votre compte et peut vous aider à décider comment attribuer le poids de l’attribution dans votre modèle personnalisé. Nous vous recommandons de comparer la gestion dynamique des balises à votre modèle personnalisé une fois par trimestre et de discuter avec votre SM des implications des modifications potentielles de votre modèle personnalisé.

Pour plus d’informations sur la variable [!DNL Marketo Measure] Modèle d’apprentissage automatique, consultez [cet article](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).
