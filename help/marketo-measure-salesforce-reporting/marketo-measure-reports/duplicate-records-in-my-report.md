---
unique-page-id: 18874634
description: Duplication d’enregistrements dans mon rapport - [!DNL Marketo Measure]
title: Doublons d’enregistrements dans mon rapport
exl-id: 4ee42371-5b67-4c69-9b49-3249f33614d0
feature: Reporting
source-git-commit: b84909fbb34a1d8f739ebeea3400ef8816e17d32
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 10%

---

# Doublons d’enregistrements dans mon rapport {#duplicate-records-in-my-report}

>[!NOTE]
>
>Vous pouvez voir des instructions spécifiant &quot;[!DNL Marketo Measure]&quot; dans la documentation, mais toujours voir &quot;[!DNL Bizible]&quot; dans votre CRM. Nous nous efforçons de mettre à jour cette version. Notre nouvelle identité (rebranding) sera bientôt répercutée dans votre CRM.

En plongeant dans le [!DNL Marketo Measure] Rapports dans [!DNL Salesforce], vous pouvez commencer à rechercher des enregistrements &quot;en double&quot; dans vos rapports. Vous allez probablement ressentir ce sentiment lorsque vous passerez en revue [!DNL Marketo Measure] rapports d’usine.

Lors de la création de rapports avec l’objet Points de contact de l’acheteur ou l’objet Point de contact de l’attribution de l’acheteur, il est important de comprendre que vous ne signalez plus le nombre de prospects, de contacts ou d’opportunités, mais que vous rapporterez plutôt le nombre de points de contact de l’achat ou de points de contact de l’attribution de l’acheteur associés à ces objets standard (prospects, contacts, opportunités).

Prenons comme exemple le rapport suivant :

Ceci est une **Contacts avec les points de contact de l’acheteur** rapport. Encore une fois, cela signifie que nous regardons le nombre de points de contact associés à un contact individuel.

![](assets/1.gif)

Comme vous pouvez le voir, il semble qu&#39;il y ait trois contacts de James Williams dans le rapport, et par conséquent vous pourriez penser, &quot;duplicatas !&quot;

Cependant, ce rapport indique le nombre de points de contact liés à James. Dans le rapport, vous pouvez constater que James possède un FT (Première touche), un LC individuel, un formulaire (Première touche de création de piste) et un point de contact PostLC (envoi de formulaire après le point de contact LC).

Si vous souhaitez comprendre le &quot;nombre de contacts&quot;, vous pouvez alors utiliser les champs &quot;Comptage - Première touche&quot;, &quot;Comptage - Création de piste&quot; ou &quot;Comptage - En forme de U&quot; pour déterminer le nombre de contacts qui ont eu des interactions marketing.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Tutorials : Stock SFDC Reports](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-102/stock-salesforce-reports){target="_blank"}
