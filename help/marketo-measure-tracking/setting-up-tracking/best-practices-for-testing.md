---
unique-page-id: 18874722
description: Bonnes pratiques relatives aux tests - [!DNL Marketo Measure]
title: Bonnes pratiques relatives aux tests
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 16%

---

# Bonnes pratiques relatives aux tests {#best-practices-for-testing}

Vous devez tester tous les différents types de formulaires dont vous avez besoin pour vous assurer que le JavaScript [!DNL Marketo Measure] fonctionne correctement.

## Processus de test recommandé {#recommended-test-process}

1. Utilisez un navigateur incognito ou effacez vos cookies entre chaque test d’envoi de formulaire _et_ en utilisant une adresse électronique différente à chaque fois.

   >[!TIP]
   >
   >Une bonne pratique consiste à utiliser un faux email contenant un élément indiquant qu’il s’agit d’un test, ainsi que l’heure de la journée. Par exemple : `testing830am@test.com`.

1. Lancez votre recherche dans un moteur de recherche (par exemple, `google.com`) ou accédez directement à un formulaire.

1. Envoyez le formulaire sur votre site web à l’aide d’une adresse électronique unique.

1. Enregistrez l’URL de la page sur laquelle vous envoyez le formulaire et l’adresse électronique utilisée.

1. Recherchez l’enregistrement créé dans votre CRM (prospect ou contact) pour cet envoi de formulaire et vérifiez qu’un point de contact a été créé.

>[!NOTE]
>
>Vous pouvez utiliser un rapport de stock [!DNL Marketo Measure], tel que Pistes avec points de contact [!DNL Marketo Measure], ou consulter la mise en page de piste/contact si vous avez choisi de mettre à jour vos mises en page avec les [!DNL Marketo Measure] détails. Le traitement des données peut prendre du temps.
