---
description: Exclusion de [!DNL Marketo Measure] des conseils Forms spécifiques pour les utilisateurs de Marketo Measure
title: Exclusion de [!DNL Marketo Measure] d’un Forms spécifique
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
hidefromtoc: 'yes'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%
---
# Exclusion de [!DNL Marketo Measure] d’un Forms spécifique {#excluding-marketo-measure-from-specific-forms}

Par défaut, [!DNL Marketo Measure] se joint à tous les formulaires de votre site. Cependant, tous les envois de formulaire ne doivent pas nécessairement être suivis ou inclus dans un modèle d’attribution. Cela est dû au fait que tous les remplissages de formulaire ne sont pas considérés comme « bons ». Il peut s’agir, par exemple, d’un formulaire ou d’une page de désabonnement. En outre, les formulaires de connexion ne sont généralement pas suivis, car cela diluerait le modèle d’attribution.

## Comment ajouter du code [!DNL Marketo Measure]-exclusion :  {#how-to-add-marketo-measure-exclude-code}

Pour empêcher [!DNL Marketo Measure] de suivre des formulaires spécifiques, ajoutez simplement « [!DNL Bizible-Exclude] » comme « classe » sur votre formulaire. Le code est le suivant :

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
