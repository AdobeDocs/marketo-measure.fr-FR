---
description: Exclusion  [!DNL Marketo Measure]  du Forms spécifique - [!DNL Marketo Measure]
title: Exclure  [!DNL Marketo Measure]  de formulaires spécifiques
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 4%

---


# Exclusion de [!DNL Marketo Measure] d’un Forms spécifique {#excluding-marketo-measure-from-specific-forms}

Par défaut, [!DNL Marketo Measure] se joint à tous les formulaires de votre site. Cependant, tous les envois de formulaire ne doivent pas nécessairement être suivis ou inclus dans un modèle d’attribution. Cela est dû au fait que tous les remplissages de formulaire ne sont pas considérés comme « bons ». Il peut s’agir, par exemple, d’un formulaire ou d’une page de désabonnement. En outre, les formulaires de connexion ne sont généralement pas suivis, car cela diluerait le modèle d’attribution.

## Comment ajouter du code [!DNL Marketo Measure]-exclusion :  {#how-to-add-marketo-measure-exclude-code}

Pour empêcher [!DNL Marketo Measure] de suivre des formulaires spécifiques, ajoutez simplement « [!DNL Bizible-Exclude] » comme « classe » sur votre formulaire. Le code est le suivant :

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
