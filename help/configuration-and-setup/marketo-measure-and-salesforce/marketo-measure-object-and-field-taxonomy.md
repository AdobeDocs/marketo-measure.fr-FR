---
unique-page-id: 18874584
description: "[!DNL Marketo Measure] Taxonomie des objets et des champs - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Objet et taxonomie des champs"
exl-id: 67f1cac8-e2b4-45cc-b1c9-58bf4e1a760d
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Taxonomie des objets et des champs [!DNL Marketo Measure] {#marketo-measure-object-and-field-taxonomy}

Vous trouverez ci-dessous un diagramme de flux qui représente la façon dont [!DNL Marketo Measure] objets personnalisés sont associés à [!DNL Salesforce] objets standard.

![](assets/1-2.png)

Pour l&#39;image en taille réelle, [cliquez ici](assets/bizible-object-and-field-taxonomy-graph-full.png).

Les définitions des champs [!DNL Marketo Measure] qui vivent dans chaque objet [&#x200B; se trouvent ici](/help/introduction-to-marketo-measure/overview-resources/glossary-of-marketo-measure-fields.md).

## Questions fréquentes {#faq}

**Quelle est la logique dans les flèches ?**

Chaque flèche décrit la relation entre un objet et l’autre. Par exemple, vous pouvez constater que la personne [!DNL Marketo Measure] remplit les champs sur l’objet de piste standard [!DNL Salesforce]. Si elle pointe vers elle, alors cela signifie qu&#39;elle remplit l&#39;extrémité de réception de la flèche.

**Qu&#39;est-ce que la [!DNL Marketo Measure] personne ?**

Il s’agit d’un objet [!DNL Marketo Measure] personnalisé dans [!DNL Salesforce] qui lie les points de contact de l’acheteur aux pistes et aux contacts.

**Qu’est-ce que [!DNL Bizible].JS ?**

C’est notre JavaScript personnalisé que nous utilisons pour effectuer le suivi des informations web qu’une personne possède sur un site spécifique.

**Qu’est-ce que le tableau de bord du ROI marketing ?**

Il s’agit d’un tableau de bord personnalisé de canaux marketing qui réside dans l’application [!DNL Marketo Measure]. Vous pouvez y accéder en vous rendant dans l’onglet [!DNL Marketo Measure] de [!DNL Salesforce].
