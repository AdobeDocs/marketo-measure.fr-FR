---
unique-page-id: 18874722
description: Bonnes pratiques relatives aux tests - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques relatives aux tests
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 1%

---

# Bonnes pratiques relatives aux tests {#best-practices-for-testing}

Vous devez tester tous les différents types de formulaires pour vous assurer que la variable [!DNL Marketo Measure] JavaScript fonctionne correctement.

## Processus de test recommandé {#recommended-test-process}

1. Utilisez un navigateur incognito ou effacez vos cookies entre chaque test d’envoi de formulaire. _et_ utilisez une adresse email différente à chaque fois.

   >[!TIP]
   >
   >Une bonne pratique consiste à utiliser un faux email contenant un élément indiquant qu’il s’agit d’un test, ainsi que l’heure de la journée. Par exemple: `testing830am@test.com`.

1. Lancez votre recherche dans un moteur de recherche (par exemple, `google.com`) ou accéder directement à un formulaire.

1. Envoyez le formulaire sur votre site web à l’aide d’une adresse électronique unique.

1. Enregistrez l’URL de la page sur laquelle vous envoyez le formulaire et l’adresse électronique utilisée.

1. Recherchez l’enregistrement créé dans votre CRM (prospect ou contact) pour cet envoi de formulaire et vérifiez qu’un point de contact a été correctement créé.

>[!NOTE]
>
>Vous pouvez utiliser une [!DNL Marketo Measure] rapport de stock, tel que Pistes avec [!DNL Marketo Measure] Points de contact ou examinez la mise en page de piste/contact si vous avez choisi de mettre à jour vos mises en page avec [!DNL Marketo Measure] détails. Le traitement des données peut prendre du temps.
