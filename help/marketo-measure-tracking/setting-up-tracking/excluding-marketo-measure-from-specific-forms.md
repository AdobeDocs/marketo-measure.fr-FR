---
unique-page-id: 18874783
description: Exclusion de [!DNL Marketo Measure] de Forms spécifique - [!DNL Marketo Measure]
title: Exclure  [!DNL Marketo Measure]  de formulaires spécifiques
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 4%

---

# Exclusion de [!DNL Marketo Measure] d’une Forms spécifique {#excluding-marketo-measure-from-specific-forms}

Par défaut, [!DNL Marketo Measure] se joint à tous les formulaires de votre site. Cependant, toutes les soumissions de formulaires ne doivent pas nécessairement être suivies ou incluses dans un modèle d’attribution. Cela est dû au fait que tous les remplissages de formulaire ne sont pas considérés comme &quot;bons&quot;. Il s’agit, par exemple, d’une page/d’un formulaire de désabonnement. En outre, les formulaires de connexion ne sont généralement pas suivis, car ils dilueraient le modèle d’attribution.

## Comment ajouter [!DNL Marketo Measure]-exclure le code :  {#how-to-add-marketo-measure-exclude-code}

Pour empêcher [!DNL Marketo Measure] d’effectuer le suivi de formulaires spécifiques, ajoutez simplement &quot;[!DNL Bizible-Exclude]&quot; en tant que &quot;classe&quot; sur votre formulaire. Le code est le suivant :

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
