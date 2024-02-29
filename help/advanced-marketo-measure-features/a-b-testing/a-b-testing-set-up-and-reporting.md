---
unique-page-id: 18874773
description: Configuration des tests A/B et création de rapports - [!DNL Marketo Measure]
title: Configuration des tests A/B et création de rapports
exl-id: 9a3f0731-5909-4fbf-a35a-9608ff561061
feature: A/B Testing
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 5%

---

# Configuration des tests A/B et création de rapports {#a-b-testing-set-up-and-reporting}

La variable [!DNL Marketo Measure] L’intégration des tests A/B vous permet de suivre l’impact de vos recettes sur les recettes [Optimisation](https://www.optimizely.com/){target="_blank"} et des expériences sur site VWO. Cet article fournit des instructions sur la manière d’ajouter des [!DNL Marketo Measure] les sections Test A/B du prospect, [!UICONTROL Contact], Cas et [!UICONTROL Opportunité] mises en page. Les pratiques générales de création de rapports et les recommandations d’exécution sont également abordées. [!DNL Marketo Measure] Types de rapports A/B.

## Configuration {#set-up}

Ajoutez la variable [!DNL Marketo Measure] Sections Test A/B sur les pistes, les contacts, les dossiers et les opportunités. [!DNL Marketo Measure] L’intégration des tests A/B vous permet de suivre l’impact de vos recettes sur les recettes [Optimisation](https://www.optimizely.com/){target="_blank"} and [VWO](https://vwo.com/){target="_blank"} expériences sur site.

1. Vérification de l’utilisation du package [!DNL Marketo Measure] v3.9 ou version ultérieure. Vous pouvez le faire en accédant à [!UICONTROL Salesforce] >[!UICONTROL Configuration] > [!UICONTROL Packages installés].
1. Modifiez la mise en page de la piste et ajoutez le **[!DNL Marketo Measure]Tests A/B** Liste associée à la page.

   ![](assets/1.png)

1. Cliquez sur le bouton [!UICONTROL Forme] bouton . Supprimez le champ &quot;Id&quot; du stock de la liste des champs Sélectionnés. Ajouter **[!UICONTROL Expérience]**, **[!UICONTROL Variation]**, et **[!UICONTROL DateReported]** des champs. Modifier &quot;[!UICONTROL Tri par]&quot; à **[!UICONTROL Date de rapport]**, puis sélectionnez **[!UICONTROL Descendant]** dans la liste déroulante.

   ![](assets/2.png)

1. Sous [!UICONTROL Boutons], décochez **[!UICONTROL Nouveau]**.

   ![](assets/3.png)

1. Contactez votre [!DNL Marketo Measure] rep ou [Prise en charge de Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} pour activer la fonction.

## Production de rapports {#reporting}

Les clients ont accès à quelques [!DNL Marketo Measure] Types de rapports A/B qui vous permettent de créer des rapports sur les tests A/B par rapport aux pistes, contacts et opportunités :

* [!DNL Marketo Measure] A/BTests
* [!DNL Marketo Measure] A/BTests avec contact
* [!DNL Marketo Measure] A/BTests avec plomb
* [!DNL Marketo Measure] A/BTests avec opportunité

![](assets/4.png)

Les types de rapports A/B sont utilisés pour déterminer sur quel prospect ou contact ou opportunité a été exposé à un test A/B. Ces rapports indiquent également le montant des recettes liées à une opportunité exposée à un test A/B.

Il est important de noter qu’Optimizely/VWO est une plateforme de variation de contenu et non un canal marketing. Par conséquent, ces [!DNL Marketo Measure] Les types de rapports A/B sont utilisés différemment des rapports Points de contact d’achat. Les types de rapports Points de contact de l’utilisateur sont utilisés pour déterminer quel canal marketing (publicité payante, direct web, social) a conduit une piste ou un contact vers une page spécifique. Cependant, [!DNL Marketo Measure] Les types de rapports A/B ne peuvent pas être utilisés pour déterminer de quelle façon une variation a influencé une piste ou une opportunité. Comme une variation de test A/B n’est pas un canal, les détails de la variation n’apparaissent pas sur le point de contact de l’utilisateur.

Voici quelques champs recommandés à utiliser lors de la création de rapports sur un test A/B afin d’améliorer la clarté et les informations :

* piste convertie
* Expérience
* ID d’expérience
* Variation
* ID de variation
* Date de rapport

## [!DNL Salesforce] Exemples de rapports {#salesforce-example-reports}

**[!DNL Marketo Measure]Test A/B avec piste**

![](assets/5.png)

**[!DNL Marketo Measure]Test A/B avec opportunité**

![](assets/6.png)
