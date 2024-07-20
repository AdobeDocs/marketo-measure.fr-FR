---
unique-page-id: 18874582
description: "[!DNL Marketo Measure] Objets Salesforce - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Objets Salesforce"
exl-id: d5d6f334-6531-40fa-b043-75b49d8f43d5
feature: Salesforce
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 4%

---

# Objets Salesforce de [!DNL Marketo Measure] {#marketo-measure-salesforce-objects}

>[!NOTE]
>
>Des instructions spécifiant « [!DNL Marketo Measure] » peuvent s’afficher dans la documentation. Toutefois, votre gestion de la relation client (CRM) mentionne encore « Bizible ». Nous nous efforçons de mettre cela à jour. Notre nouvelle identité de marque (rebranding) sera bientôt répercutée dans votre CRM.

Lorsque [!DNL Marketo Measure] est installé dans [!DNL Salesforce] (SFDC), plusieurs objets [!DNL Marketo Measure] personnalisés sont ajoutés. Cet article explique plusieurs de ces objets [!DNL Marketo Measure] personnalisés. Voici quelques objets ajoutés à [!DNL Salesforce] :[!DNL Marketo Measure]

* [Buyer Touchpoint](#touchpoint)
* [Buyer Attribution Touchpoint](#attribution)
* [[!DNL Marketo Measure] Personne](#person)
* [[!DNL Marketo Measure] Tests A/B](#ab)
* [[!DNL Marketo Measure] Événements](#events)

Les points de contact capturés par les éléments dont vous souhaitez effectuer le suivi écrivent dans les objets personnalisés créés par l’installation du package [!DNL Bizible Salesforce].

[!DNL Marketo Measure] Les objets sont associés à des objets [!DNL Salesforce] standard spécifiques. Vous pouvez ainsi créer des rapports sur les objets [!DNL Marketo Measure] et [!DNL Salesforce] ensemble. Le tableau ci-dessous indique à quel objet [!DNL Salesforce] l’objet [!DNL Marketo Measure] se rapporte.

![](assets/1-1.png)

## Buyer Touchpoint {#buyer-touchpoint}

L’objet [!UICONTROL Buyer Touchpoint] (BT) raconte l’histoire marketing d’un individu. Il regroupe toutes les données relatives aux points de contact marketing générés par les Leads et les contacts. Le BT vous présente des informations telles que le canal marketing d’où provient le point de contact ou la campagne publicitaire qui a amené ce prospect/contact particulier à votre site web.

L’objet BT est visible sur les pages Leads et Contacts sous la forme d’une **Liste connexe** (voir l’image ci-dessous).

![](assets/2-1.png)

La liste associée BT affiche tous les points de contact qui appartiennent au prospect ou au contact. La liste contient des champs [!DNL Marketo Measure] personnalisés qui fournissent des détails supplémentaires sur chaque point de contact. En cliquant sur le numéro d’Buyer Touchpoint ID, vous accédez à la page Détails de Buyer Touchpoint, qui fournit encore plus de détails sur le point de contact, comme la première page web visitée par le prospect/contact au cours de cette session web (**landing page**).

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

L’objet [!UICONTROL Buyer Attribution Touchpoint] raconte l’histoire des interactions marketing de vos contacts liés à une opportunité. Il affiche les données *attribution* liées aux points de contact marketing. Cet objet vous permet de voir le montant du crédit de recettes attribué à chaque point de contact marketing. Le type de modèle d’attribution que vous utilisez détermine le pourcentage de recettes attribué aux points de contact.

Les points de contact d’attribution de l’acheteur (BAT) ne sont créés qu’une seule fois qu’une opportunité est créée relative à des contacts qui disposent de données Buyer Touchpoint (BT). BAT ne sera pas créé sans opportunité. Une fois l’opportunité créée, l’objet BAT utilise le champ [!DNL Salesforce] *Amount* sur l’opportunité pour comprendre le montant des recettes à attribuer aux points de contact.

Un **workflow** doit être créé si vous utilisez un [champ Montant personnalisé](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md) pour afficher les recettes sur l’objet d’opportunité. [!DNL Marketo Measure] n’est pas en mesure de lire les informations affichées dans les champs Montant personnalisés et, par conséquent, ne peut pas renseigner les données d’attribution de recettes sur les points de contact. Ce workflow utilisera le champ **[!DNL Marketo Measure]Montant de l’opportunité**, l’un des champs personnalisés [!DNL Marketo Measure], pour mapper la valeur des recettes du champ Montant personnalisé au champ Montant de l’opportunité.

![](assets/3-1.png)

L’objet BAT est visible sur les objets [!UICONTROL Opportunity], [!UICONTROL Contact] et [!UICONTROL Account] Object as a Related List. Cette liste affiche tous les points de contact avec les données d’attribution appartenant à une opportunité. Cliquez sur le Buyer Attribution Touchpoint ID pour accéder à la page Détails de Buyer Attribution Touchpoint. Vous pourrez y voir des données d’attribution plus spécifiques et des informations sur l’origine du point de contact (similaires à ce qui est fourni à partir de l’objet Buyer Touchpoint).

## [!DNL Marketo Measure] Personne {#marketo-measure-person}

L’objet de personne [!DNL Marketo Measure] associe les objets Lead et Contact. Salesforce ne permet pas de créer des rapports à l’aide de l’objet Lead et Contact dans le même rapport. En fonction de l’objet Lead et contact, la personne [!DNL Marketo Measure] vous permet de créer des rapports sur les deux objets dans le même rapport. Cela s’avère particulièrement utile lorsqu’une piste a été convertie en contact. Sur un enregistrement de personne [!DNL Marketo Measure], vous verrez une recherche de l’enregistrement de piste et/ou de contact correspondant, une liste associée des points de contact liés à la personne et l’ID de personne (qui est toujours l’adresse électronique du prospect/contact). Puisque la personne [!DNL Marketo Measure] se rapporte à l’objet Lead &amp; Contact, il n’y aura jamais d’enregistrement [!DNL Marketo Measure] de personne lié à un Buyer Attribution Touchpoint. Vous trouverez ci-dessous un exemple d’enregistrement de personne [!DNL Marketo Measure] dans Salesforce :

![](assets/4.png)

## [!DNL Marketo Measure] Test A/B {#marketo-measure-a-b-test}

Si vous exécutez des tests A/B par le biais de [!DNL Optimizely] ou de VWO (Visual Web Optimizer), vous pouvez connecter ces comptes à votre compte [!DNL Marketo Measure] pour afficher les données de test A/B dans Salesforce. L’objet de test A/B [!DNL Marketo Measure] vous permet essentiellement de prendre les données de test A/B d’ Optimizely/VWO et de lier les données aux Leads et contacts.

![](assets/5.png)

L’ [!DNL Marketo Measure] objet de test A/B s’affiche sous forme d’une liste associée sur les pages [!UICONTROL Leads], [!UICONTROL Contacts] et [!UICONTROL Opportunity] . La liste répertorie toutes les expériences et variations que vous exécutez via Optimizely ou VWO et vous permet de voir les expériences/variations en rapport avec des pistes et des contacts spécifiques.

## [!DNL Marketo Measure] Événements {#marketo-measure-events}

L’objet d’événements [!DNL Marketo Measure] vous permet de suivre des événements spécifiques qui se produisent sur votre site web. Pour effectuer le suivi d’événements spécifiques qui se produisent sur votre site web, du code personnalisé doit être ajouté à vos pages en plus du code JavaScript [!DNL Marketo Measure]. Les informations capturées seront affichées dans la liste [!DNL Marketo Measure] liée aux objets, qui se trouve sur les pages [!UICONTROL Leads], [!UICONTROL Contacts] et [!UICONTROL Opportunity] . L’ [!DNL Marketo Measure] objet d’événements *n’est pas* lié aux données d’attribution. L’objectif de cet objet est de voir si des personnes effectuent des actions spécifiques sur votre site web.

## [!DNL Marketo Measure] Fields {#marketo-measure-fields}

Les données capturées par le JavaScript [!DNL Marketo Measure] sont transmises aux champs personnalisés [!DNL Marketo Measure] dans les objets [!DNL Marketo Measure]. Certains champs ne sont présents que sur certains objets. Vous pouvez consulter le [glossaire de [[!DNL Marketo Measure] champs]](/help/introduction-to-marketo-measure/overview-resources/glossary-of-marketo-measure-fields.md) et une [visualisation des  [!DNL Marketo Measure] objets](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md) associés.

## [!DNL Marketo Measure] Rapports et tableaux de bord {#marketo-measure-reports-and-dashboards}

Les [!DNL Marketo Measure] rapports et tableaux de bord ajoutés à votre [!DNL Salesforce] vous offrent des fonctionnalités de rapports et de visualisation de données prêtes à l’emploi. Il s’agit de rapports de base [!DNL Marketo Measure] qui vous permettent d’organiser, d’analyser et de comprendre rapidement les données de point de contact.
