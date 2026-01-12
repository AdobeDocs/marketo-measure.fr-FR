---
description: Différence entre les Buyer Touchpoints et les Buyer Attribution Touchpoints -  [!DNL Marketo Measure]
title: Différence entre les points de contact acheteur et les points de contact d’attribution acheteur
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
feature: Touchpoints
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 100%

---


# Différence entre les points de contact acheteur et les points de contact d’attribution acheteur {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Découvrez ce qui définit un point de contact acheteur (BT) et un point de contact d’attribution acheteur (BAT), les différences entre les deux et les réponses aux questions fréquemment posées.

La différence principale entre les points de contact acheteur et les points de contact d’attribution acheteur réside dans leur relation avec les objets [!DNL Salesforce]. Les BT se rapportent aux objets Prospect, Contact et Dossier, mais pas à Opportunité. En d’autres termes, il n’y aura jamais de revenus associés aux Buyer Touchpoints.

Alors que les objets Buyer Attribution Touchpoint sont liés aux objets Contact, Compte et Opportunité, mais pas à l’objet Prospect, les Buyer Attribution Touchpoints ne sont pas liés aux Prospects. L’objet BAT permet de lier des revenus à des interactions marketing spécifiques.

Différence entre BT et BAT :

<table>
 <colgroup>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <td>Point de contact acheteur (BT)</td>
   <td>Point de contact d’attribution acheteur (BAT)</td>
  </tr>
  <tr>
   <td>
    <ul>
     <li>Fait référence à des objets Prospect, Contact et Dossier.</li>
     <li>Ne peut pas être lié à des objets Opportunité.</li>
     <li>Les recettes ne sont pas associées à un point de contact acheteur.</li>
    </ul></td>
   <td>
    <ul>
     <li>Fait référence à des objets Contact, Compte et Opportunité.</li>
     <li>Ne peut pas être lié à des objets Prospect.</li>
     <li>Étant donné qu’un point de contact d’attribution acheteur est associé à une opportunité, tous les BAT sont associés à des recettes.</li>
    </ul></td>
  </tr>
 </tbody>
</table>

## Questions fréquentes {#faq}

**À quel moment un point de contact acheteur devient-il un point de contact d’attribution acheteur ?**

Un BT devient un BAT une fois qu’il est associé à un contact lui-même associé à une opportunité. Ce qu’il faut comprendre, c’est qu’une interaction marketing spécifique peut être liée à un BT et à un BAT.

**Un point de contact acheteur peut-il avoir une position correspondant à la création d’une opportunité ?**

Un point de contact acheteur peut uniquement avoir trois positions : Premier contact (FT), Création de prospects (LC) ou Envoi de formulaire (points de contact intermédiaires). Puisque les BT ne sont pas liés à des opportunités, ils ne peuvent pas avoir de position de point de contact correspondant à la création ou à la fermeture d’une opportunité.

**Comment les données Buyer Touchpoint sont-elles exploitées ?**

En règle générale, les clientes et clients utilisent les données Buyer Touchpoint pour comprendre l’engagement en haut et au milieu de l’entonnoir. En d’autres termes, les utilisateurs et utilisatrices de [!DNL Marketo Measure] savent qui envoie des formulaires, qui visite leur site, quel article de blog est souvent consulté, quelle publicité AdWords amène à une conversion des prospects, etc. Les données de point de contact acheteur sont particulièrement utiles pour comprendre l’engagement de vos prospects et contacts.

**À quoi ressemble un point de contact acheteur dans Salesforce ?**

Voici une copie d’écran d’un BT dans [!DNL Salesforce] :

![](assets/buyer-touchpoints-and-buyer-attribution-touchpoints-1.png){width="600" zoomable="yes"}

**À quoi ressemble un point de contact d’attribution acheteur dans Salesforce ?**

Voici une copie d’écran d’un BAT dans [!DNL Salesforce] :

![](assets/buyer-touchpoints-and-buyer-attribution-touchpoints-2.png){width="600" zoomable="yes"}
