---
unique-page-id: 18874646
description: Différence entre les points de contact des acheteurs et les points de contact d’attribution des acheteurs - [!DNL Marketo Measure] - Documentation du produit
title: Différence entre les points de contact d’un achat et les points de contact d’attribution d’un achat
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Différence entre les points de contact d’un achat et les points de contact d’attribution d’un achat {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Découvrez ce qui définit un point de contact d’achat (BT) et un point de contact d’attribution d’achat (BAT), les différences entre les deux et répondez aux questions courantes.

La distinction essentielle entre les points de contact d’achat et les points de contact d’attribution d’achat réside dans leur relation avec [!DNL Salesforce] Objets. Les BAT se rapportent aux objets de piste, de contact et de cas, mais pas à l’objet Opportunity . En d’autres termes, il n’y aura jamais de recettes associées aux points de contact de l’acheteur.

Bien que l’objet point de contact d’attribution de l’achat soit lié aux objets de contact, de compte et d’opportunité, mais pas à l’objet de piste. En d’autres termes, il n’y aura jamais de points de contact d’attribution d’achat liés aux pistes. L’objet BAT est l’endroit où les recettes sont liées à des interactions marketing spécifiques.

Différence entre BT et BAT :

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td>Point de contact de l’utilisateur (BT)</td> 
   <td>Point de contact d’attribution de l’acheteur (BAT)</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>Se rapporte aux objets de piste, de contact et de cas</li> 
     <li>N’est pas lié à l’objet d’opportunité</li> 
     <li>Les recettes ne sont pas associées à un point de contact d’achat</li> 
    </ul></td> 
   <td> 
    <ul> 
     <li>Se rapporte aux objets Contact, Compte et Opportunité</li> 
     <li>N’est pas lié à l’objet de piste</li> 
     <li>Comme un point de contact d’attribution d’achat est associé à une opportunité, tous les AT ont des recettes qui leur sont associées.</li> 
    </ul></td> 
  </tr> 
 </tbody> 
</table>

## FAQ {#faq}

**Quand un point de contact d’achat devient-il un point de contact d’attribution d’achat ?**

Un BT devient un MAT une fois qu’il est associé à un Contact associé à une Opportunité. Une chose très importante à comprendre est qu&#39;une interaction marketing spécifique peut être un BT et une MAT.

**Un point de contact d’achat peut-il avoir une position de point de contact pour la création d’opportunités ?**

Un point de contact d’achat a uniquement une position de point de contact Première touche (FT), Création de piste (LC) ou Envoi de formulaire (points de contact intermédiaires). Puisque les BT ne sont pas liés aux opportunités, il n&#39;est pas possible qu&#39;un BT ait une position de point de contact de la création d&#39;opportunités ou de fermeture.

**Comment les données du point de contact de l’achat sont-elles exploitées ?**

En règle générale, les clients exploitent les données du point de contact de l’acheteur pour comprendre les champs Entonnoir et milieu de l’engagement Entonnoir. Signification [!DNL Marketo Measure] les utilisateurs savent qui envoie des formulaires, qui consulte leur site, quelle publication de blog se comporte bien, ce qu’AdWords et génère entraîne la conversion, etc. Les données de point de contact de l’acheteur sont très utiles pour comprendre l’engagement de vos Leads &amp; Contacts.

**À quoi ressemble un point de contact d’achat dans Salesforce ?**

Voici une capture d&#39;écran d&#39;un BT dans [!DNL Salesforce]:

![](assets/1.png)

**À quoi ressemble un point de contact d’attribution d’achat dans Salesforce ?**

Voici une capture d’écran d’une AT dans [!DNL Salesforce]:

![](assets/2.png)
