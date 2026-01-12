---
description: Bonnes pratiques pour les tests - [!DNL Marketo Measure]
title: Bonnes pratiques relatives aux tests
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 19%

---


# Bonnes pratiques relatives aux tests {#best-practices-for-testing}

Vous devez tester tous les différents types de formulaires dont vous disposez pour vous assurer du bon fonctionnement de [!DNL Marketo Measure] JavaScript.

## Processus de test recommandé {#recommended-test-process}

1. Utilisez un navigateur incognito ou effacez vos cookies entre chaque test d’envoi de formulaire _et_ utilisez une adresse e-mail différente à chaque fois.

   >[!TIP]
   >Une bonne pratique consiste à utiliser un faux e-mail contenant un élément indiquant qu’il s’agit d’un test, ainsi que l’heure. Par exemple : `testing830am@test.com`.

1. Lancez votre recherche dans un moteur de recherche (par exemple, `google.com`) ou accédez directement à un formulaire.

1. Envoyez le formulaire sur votre site web à l’aide d’une adresse e-mail unique.

1. Enregistrez l’URL de la page sur laquelle vous envoyez le formulaire et l’adresse e-mail utilisée.

1. Recherchez l’enregistrement créé dans votre CRM (prospect ou contact) pour cet envoi de formulaire et vérifiez qu’un point de contact a été créé.

>[!NOTE]
>Vous pouvez utiliser un rapport de stock [!DNL Marketo Measure] tel que les leads avec des points de contact [!DNL Marketo Measure] ou consulter la mise en page du lead/contact si vous avez choisi de mettre à jour vos mises en page avec des détails [!DNL Marketo Measure]. Le traitement des données peut prendre un certain temps.
