---
unique-page-id: 18874586
description: Glossaire des champs Marketo Measure - Marketo Measure - Documentation du produit
title: Glossaire des champs Marketo Measure
exl-id: 8e23b102-6d4f-4919-b361-04d1b184e710
feature: Fundamentals
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '3213'
ht-degree: 99%

---

# Glossaire des champs Marketo Measure {#glossary-of-marketo-measure-fields}

Ce glossaire détaille tous les champs ajoutés à votre instance Salesforce à partir du package de base Marketo Measure. Vous trouverez également des informations sur la correspondance entre les objets et les champs, ainsi que sur la manière dont chaque champ est renseigné.

Pour une carte à laquelle chaque champ Marketo Measure se rapporte, [cliquez ici](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

[A](#a) · [B](#b) · [C](#c) · [D](#d) · [E](#e) · [F](#f) · [G](#g) · H · I · J · [K](#k) · [L](#l) · [M](#m) · N · [O](#o) · [P](#p) · Q · [R](#r) · [S](#s) · [T](#t) · [U](#u) · [V](#v) · W · X · Y · Z

## A {#a}

**Compte** | Correspond aux points de contact d’attribution acheteur

Ce champ est renseigné avec le nom du compte associé au BAT.

**Identifiant de la campagne publicitaire** | Correspond aux points de contact acheteur et aux points de contact d’attribution acheteur

Ce champ peut être renseigné de trois façons :

`1)` Si le point de contact provient du référencement payant (AdWords ou Bing Ads), l’identifiant de campagne publicitaire de la plateforme s’affiche.

`2)` Si le point de contact ne provient pas du référencement payant, le champ est renseigné à l’aide de la valeur utm_campaign de l’URL de la page de destination.

Exemple : `http://info.marketomeasure.com/adwords-for-lead-generation?utm_source=Event&utm_medium=booth&utm_campaign=Marketo%20Virtual%20Event%20sep2014`

Dans cet exemple, l’identifiant de campagne publicitaire est : __GAId__ Marketo Virtual Event sept2014.

`3)` Si le point de contact provient d’une campagne Salesforce hors ligne (une conférence, un dîner, etc.), l’identifiant de campagne publicitaire correspond à l’identifiant de la campagne en question.

Si aucun des cas ci-dessus ne correspond, ce champ reste vide.

**Nom de la campagne publicitaire** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant (AdWords ou Bing Ads), ce champ reprend le nom de la campagne publicitaire de la plateforme.

`2)` Si le point de contact ne provient pas du référencement payant et que l’URL de la page de destination contient une valeur pour utm_campaign, elle est reprise ici.

`3)` Si le point de contact provient d’une campagne Salesforce, son nom s’affiche ici.

`4)` Ce champ est renseigné avec le nom de campagne défini pour les points de contact générés à partir des activités, comme défini dans votre compte Marketo Measure.

Si aucun des cas ci-dessus ne correspond, ce champ reste vide.

**Nom de la campagne publicitaire (FT)** | Point de contact acheteur

Ce champ est renseigné de la même manière que pour le nom de la campagne publicitaire. Cependant, il a la particularité d’indiquer spécifiquement le nom de la campagne publicitaire qui a généré le premier point de contact.

**Nom de la campagne publicitaire (LC)** | Point de contact acheteur

Ce champ est renseigné de la même manière que pour le nom de la campagne publicitaire. Cependant, il a la particularité d’indiquer spécifiquement le nom de la campagne publicitaire qui a généré le point de contact à l’origine de la création du prospect.

**Contenu publicitaire** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant (AdWords/Bing Ads), ce champ affiche le texte publicitaire complet correspondant à l’annonce sur la plateforme.

`2)` Si le point de contact ne provient pas du référencement payant, ce champ affiche la valeur utm_content dans l’URL de la page de destination.

`3)` Ce champ est renseigné avec la valeur Objet de l’activité qui a généré le point de contact.

Si aucun des cas ci-dessus ne correspond, ce champ reste vide.

**URL de destination de la publicité** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant, ce champ affiche la destination de l’URL vers laquelle l’utilisateur est redirigé après avoir cliqué sur la publicité dans le moteur de recherche.

Si le point de contact ne provient pas du référencement payant, ce champ reste vide.

**Identifiant du groupe publicitaire** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant, l’identifiant du groupe publicitaire AdWords/Bing Ads s’affiche ici.

Si le point de contact ne provient pas du référencement payant, ce champ reste vide.

**Nom du groupe publicitaire** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant, le nom du groupe publicitaire AdWords/Bing Ads s’affiche ici.

Si le point de contact ne provient pas du référencement payant, ce champ reste vide.

**Identifiant publicitaire** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant, l’identifiant publicitaire AdWords/Bing Ads s’affiche ici.

`2)` Si le point de contact est généré à partir d’une activité CRM, ce champ est renseigné avec l’identifiant externe d’activité.

Si le point de contact ne provient pas du référencement payant, ce champ reste vide.

**Pourcentage d’attribution (modèle personnalisé)** | Point de contact d’attribution acheteur

Si vous utilisez un modèle d’attribution personnalisé, ce champ affiche le pourcentage de recettes attribuées à un point de contact en fonction des valeurs définies dans votre modèle.

Si vous n’utilisez pas de modèle personnalisé, ce champ reste vide.

**Pourcentage d’attribution (premier contact)** | Point de contact d’attribution acheteur

Ce champ affiche le pourcentage de recettes attribuées à un point de contact en fonction d’un modèle basé sur le premier contact.

**Pourcentage d’attribution (modèle complet)** | Point de contact d’attribution acheteur

Ce champ affiche le pourcentage de recettes attribuées à un point de contact en fonction d’un modèle en chemin complet.

**Pourcentage d’attribution (création de prospects)** | Point de contact d’attribution acheteur

Ce champ affiche le pourcentage de recettes attribuées à un point de contact en fonction d’un modèle basé sur la création de prospects.

**Pourcentage d’attribution (modèle en forme de U)** | Point de contact d’attribution acheteur

Ce champ affiche le pourcentage de recettes attribuées à un point de contact en fonction d’un modèle en forme de U.

**Pourcentage d’attribution (modèle en forme de W)** | Point de contact d’attribution acheteur

Ce champ affiche le pourcentage de recettes attribuées à un point de contact en fonction d’un modèle en forme de W.

[Cliquez ici pour revenir en haut de la page.](#top)

## B {#b}

**Montant de l’opportunité Marketo Measure** | Opportunité Salesforce

Si vous utilisez un champ de montant personnalisé pour signaler les recettes d’opportunité, Marketo Measure ne peut pas le lire. Le montant de l’opportunité Marketo Measure est un champ masqué qui est utilisé pour créer un processus permettant à l’outil de lire les champs de montant personnalisés sur l’opportunité.

**Navigateur** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ indique le type de navigateur utilisé au cours de la session (Chrome, Safari, Firefox, etc.).

[Cliquez ici pour revenir en haut de la page.](#top)

## C {#c}

**Contact** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche le contact auquel le point de contact appartient.

**Valeur (modèle personnalisé)** | Point de contact d’attribution acheteur

Si vous utilisez un modèle d’attribution personnalisé, ce champ affiche, sous forme décimale, le pourcentage de crédit de revenu attribué à un point de contact en fonction des valeurs définies dans votre modèle.

Si vous n’utilisez pas de modèle personnalisé, ce champ reste vide.

**Valeur (modèle personnalisé)** | Point de contact acheteur

Si vous utilisez un modèle d’attribution personnalisé, ce champ affiche, sous forme décimale, le pourcentage de crédit d’attribution alloué à un point de contact en fonction des valeurs définies dans votre modèle. Puisque ce champ est lié à un point de contact acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

Si vous n’utilisez pas de modèle personnalisé, ce champ reste vide.

**Valeur (premier contact)** | Point de contact d’attribution acheteur

Ce champ affiche, sous forme décimale, le pourcentage de crédit de revenu alloué à un point de contact en fonction d’un modèle basé sur le premier contact.

**Valeur (premier contact)** | Point de contact acheteur

Ce champ affiche, sous forme décimale, le pourcentage de crédit d’attribution alloué à un point de contact en fonction d’un modèle basé sur le premier contact. Si le point de contact correspond au premier contact, la valeur de ce champ sera toujours 1,0 (ce qui indique un crédit d’attribution de 100 %). Dans le cas contraire, il indiquera toujours 0 (ce qui indique un crédit d’attribution de 0 %).

Puisque ce champ est lié à un point de contact acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

**Valeur (modèle en chemin complet)** | Point de contact d’attribution acheteur

Ce champ affiche, sous forme décimale, le pourcentage de recettes alloué à un point de contact en fonction d’un modèle en chemin complet.

**Valeur (création de prospects)** | Point de contact d’attribution acheteur

Ce champ affiche, sous forme décimale, le pourcentage de crédit de revenu attribué à un point de contact en fonction d’un modèle basé sur la création de prospects.

**Valeur (création de prospects)** | Point de contact acheteur

Ce champ affiche, sous forme décimale, le pourcentage du crédit d’attribution alloué à un point de contact en fonction d’un modèle basé sur la création de prospects. Si le point de contact est celui ayant permis la création du prospect, la valeur de ce champ sera toujours 1,0 (ce qui indique un crédit d’attribution de 100 %). Dans le cas contraire, il indiquera toujours 0 (ce qui indique un crédit d’attribution de 0 %).

Puisque ce champ est lié à un point de contact acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

**Valeur (modèle en forme de U)** | Point de contact d’attribution acheteur

Ce champ affiche, sous forme décimale, le pourcentage de crédit de revenu attribué à un point de contact en fonction d’un modèle en forme de U.

**Valeur (modèle en forme de U)** | Point de contact acheteur

Ce champ affiche, sous forme décimale, le pourcentage de crédit d’attribution alloué à un point de contact en fonction d’un modèle en forme de U. Dans un modèle en forme de U, le crédit est divisé entre le premier contact, la création de prospects, et tous les envois de formulaire intermédiaires qui se produisent entre ces deux premiers points.

Puisque ce champ est lié à un point de contact acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

**Valeur (modèle en forme de W)** | Point de contact d’attribution acheteur

Ce champ affiche, sous forme décimale, le pourcentage de crédit alloué à un point de contact en fonction d’un modèle en forme de W.

[Cliquez ici pour revenir en haut de la page.](#top)

## D {#d}

Date de signalement | Test A/B Marketo Measure, événement Marketo Measure

Événement Marketo Measure : date à laquelle un utilisateur a effectué une action spécifique sur votre site web, en activant un événement.

Marketo Measure ABTest : date à laquelle un utilisateur a participé à un test A/B sur votre site web.

[Cliquez ici pour revenir en haut de la page.](#top)

## E {#e}

**Nom de l’événement** | Événement Marketo Measure

Ce champ affiche le nom de l’action qui a déclenché l’événement (par exemple, une page vue).

**Valeur de l’événement** | Événement Marketo Measure

Description de l’événement (par exemple, la consultation de la page d’accueil).

**Nom de l’expérience** | Test A/B Marketo Measure

Ce champ affiche le nom de l’expérience (par exemple, un bouton de période d’évaluation).

**Identifiant de l’expérience** | Test A/B Marketo Measure

Code d’identification unique de chaque expérience.

[Cliquez ici pour revenir en haut de la page.](#top)

## F {#f}

URL de formulaire | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche une version abrégée de l’URL d’une page où le remplissage du formulaire s’est produit (sans les paramètres UTM).

URL de formulaire (brute) | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche l’URL entière de la page où le remplissage du formulaire s’est produit, avec les paramètres UTM.

[Cliquez ici pour revenir en haut de la page.](#top)

## G {#g}

Ville | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ indique le nom de la ville dans laquelle le prospect/contact a consulté votre site web. Cette valeur est extraite d’une analyse de l’adresse IP.

Pays | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ indique le nom du pays dans lequel le prospect/contact a consulté votre site web. Cette valeur est extraite d’une analyse de l’adresse IP.

Zone géographique | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ indique le nom de la zone géographique dans laquelle le prospect/contact a consulté votre site web. Cette valeur est extraite d’une analyse de l’adresse IP.

[Cliquez ici pour revenir en haut de la page.](#top)

## K {#k}

**Identifiant du mot-clé** | Point de contact acheteur, point de contact d’attribution acheteur

Si le point de contact provient du référencement payant, ce champ affiche l’identifiant du mot-clé de la plateforme publicitaire (AdWords/Bing Ads).

Dans le cas contraire, ce champ reste vide.

**Type de correspondance du mot-clé** | Point de contact acheteur, point de contact d’attribution acheteur

Si le point de contact provient du référencement payant, ce champ affiche le type de correspondance de la plateforme publicitaire (AdWords/Bing Ads).

**Texte du mot-clé** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant, ce champ affiche le texte du mot-clé de la plateforme publicitaire (AdWords/Bing Ads) OU la valeur du paramètre _bk dans l’URL de la page de destination.

Exemple : `http://info.marketomeasure.com/intro-guide-b2b-marketing-attribution?_bt=12345678&_bk=marketing%20attribution&_bm=p&gclid=ABc123def456ghi789jkl`

`2)` Si le point de contact ne provient pas du référencement payant, ce champ affiche la valeur utm_term contenue dans l’URL de la page de destination.

`http://www.marketomeasure.com/blog/lead-generation?utm_source=linkedin&utm_medium=Social&utm_campaign=ABC%20Blog&utm_content=Lead%20Gen&utm_term=lead%20gen`.

Si le point de contact ne provient pas du référencement payant ou s’il n’existe aucune valeur utm_term, ce champ reste vide.

[Cliquez ici pour revenir en haut de la page.](#top)

## L {#l}

**Page de destination** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche la version abrégée de l’URL (sans les paramètres UTM) de la première page web visitée au cours d’une session.

**Page de destination (brute)** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche la version intégrale de l’URL (avec les paramètres UTM) de la première page web visitée au cours d’une session.

**Prospect** | Point de contact acheteur, personne Marketo Measure

Ce champ affiche le nom du prospect correspondant à un point de contact.

[Cliquez ici pour revenir en haut de la page.](#top)

## M {#m}

**Canal marketing** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ vous présente le groupe général d’activités marketing ou le canal marketing auquel le point de contact appartient (par exemple, « Référencement payant », « Direct », « Réseaux sociaux », etc.). Les points de contact sont regroupés en fonction de la configuration de vos canaux dans l’application Marketo Measure. Pour plus d’informations sur les canaux marketing ou sur la configuration de vos canaux, [cliquez ici](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

**Canal marketing (chemin)** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche le canal marketing et le sous-canal auquel appartient un point de contact. Dans l’exemple ci-dessous, la valeur est Social.Linkedin, où le canal marketing est Social, et le sous-canal est LinkedIn.

![](assets/1-3.png)

**Support** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant, le support provenant d’AdWords/Bing Ads s’affiche ici (par exemple, CPC).

`2)` Si le point de contact ne provient pas du référencement payant, ce champ affiche la valeur utm_medium contenue dans l’URL de la page de destination.

`3)` Si le point de contact provient d’une campagne hors ligne, ce champ affiche le type de la campagne Salesforce.

`4)` Ce champ est renseigné avec la valeur Type d’activité correspondant à l’activité qui a généré le point de contact.

Si aucun des cas ci-dessus ne s’applique, Marketo Measure définit automatiquement une valeur.

[Cliquez ici pour revenir en haut de la page.](#top)

O

**Opportunité** | Point de contact d’attribution acheteur

Ce champ affiche l’opportunité à laquelle le BAT appartient.

[Cliquez ici pour revenir en haut de la page.](#top)

P

**Plateforme** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche le type d’ordinateur ou de téléphone ainsi que le type de système d’exploitation utilisés au cours de la session.

[Cliquez ici pour revenir en haut de la page.](#top)

R

**Page du référent** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche l’URL (sans paramètres UTM) de la dernière page web sur laquelle se trouvait le prospect/contact et qui l’a amené vers votre site web.

Par exemple :

- Si le point de contact provient du référencement payant/naturel, le champ indique l’URL du moteur de recherche.

- Si le point de contact provient des réseaux sociaux, le champ indique l’URL du site web correspondant (par exemple, LinkedIn).

**Page du référent (brute)** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche les mêmes informations que la page du référent, à la différence qu’il s’agit de la version intégrale de l’URL (avec les paramètres UTM).

**Recettes (modèle personnalisé)** | Point de contact d’attribution acheteur

Si vous utilisez un modèle d’attribution personnalisé, ce champ affiche le montant, en dollars, de recettes attribuées à un point de contact en fonction du pourcentage défini dans votre modèle.

Dans le cas contraire, le montant en dollars est de 0.

**Recettes (premier contact)** | Point de contact d’attribution acheteur

Ce champ affiche le montant, en dollars, des recettes attribuées à un point de contact en fonction du pourcentage défini dans le modèle basé sur le premier contact.

**Recettes (modèle en chemin complet)** | Point de contact d’attribution acheteur

Ce champ affiche le montant, en dollars, des recettes attribuées à un point de contact en fonction du pourcentage défini dans le modèle en chemin complet.

**Recettes (création de prospects)** | Point de contact d’attribution acheteur

Ce champ affiche le montant, en dollars, des recettes attribuées à un point de contact en fonction du pourcentage défini dans le modèle basé sur la création de prospects.

**Recettes (modèle en forme de U)** | Point de contact d’attribution acheteur

Ce champ affiche le montant, en dollars, des recettes attribuées à un point de contact en fonction du pourcentage défini dans le modèle en forme de U.

**Recettes (modèle en forme de W)** | Point de contact d’attribution acheteur

Ce champ affiche le montant, en dollars, des recettes attribuées à un point de contact en fonction du pourcentage défini dans le modèle en forme de W.

[Cliquez ici pour revenir en haut de la page.](#top)

S

**Campagne Salesforce** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ indique la campagne Salesforce à laquelle le point de contact appartient.

**Expression de recherche** | Point de contact acheteur, point de contact d’attribution acheteur

Si le point de contact provient du référencement payant ou naturel, ce champ indique l’expression saisie dans le moteur de recherche. Cependant, pour des raisons de confidentialité, ces informations ne sont généralement pas disponibles.

**Segment** | Point de contact d’attribution acheteur

Ce champ indique les segments auxquels le point de contact appartient, ce qui dépend de la manière dont vous avez configuré vos règles de segmentation dans l’application Marketo Measure.

[Cliquez ici pour revenir en haut de la page.](#top)

T

**Date du point de contact** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient d’une source en ligne, ce champ affiche la date et l’heure de l’événement.

`2)` Si le point de contact provient d’un événement hors ligne, ce champ affiche la date et l’heure définies dans la campagne Salesforce ou à partir du champ de date sélectionné dans les règles de synchronisation de campagne.

`3)` Si le point de contact provient d’une activité, ce champ affiche la date et l’heure du champ sélectionné dans les règles de l’activité.

**Date du point de contact (FT)** | Point de contact acheteur

Il s’agit du même champ que « Date du point de contact », mais il indique spécifiquement la date et l’heure auxquelles le premier contact s’est produit.

**Date du point de contact (LC)** | Point de contact acheteur

Il s’agit du même champ que « Date du point de contact », mais il indique spécifiquement la date et l’heure auxquelles le prospect a été créé.

**Position du point de contact** | Point de contact acheteur, point de contact d’attribution acheteur

Ce champ affiche la position du point de contact. La position du point de contact reflète les principaux jalons du parcours client (FT, Formulaire, LC, OC, Terminé). La position du point de contact dépend du moment où il est survenu dans le parcours client. Un seul point de contact peut avoir plusieurs positions. Les différentes positions sont les suivantes :

Premier contact (FT) : la toute première interaction marketing qu’une personne a avec votre marque.

Création de prospects (LC) : toute première interaction marketing connue (généralement un envoi de formulaire ou l’inclusion dans une campagne Salesforce).

Formulaire : lorsqu’un visiteur remplit un formulaire en ligne.

Création d’opportunité (OC) : interaction marketing la plus proche du moment où l’opportunité est créée.

Terminée : interaction marketing la plus proche de la clôture de l’opportunité (qu’elle ait débouché sur une vente ou non).

**Source du point de contact** | Point de contact acheteur, point de contact d’attribution acheteur

`1)` Si le point de contact provient du référencement payant, ce champ affiche le nom de la plateforme publicitaire (AdWords/Bing Ads).

`2)` Si le point de contact provient du référencement naturel, ce champ indique le nom du moteur de recherche.

`3)` Si les deux premiers scénarios ne s’appliquent pas et qu’une valeur utm_source est présente dans l’URL de la page de destination associée au point de contact, cette valeur est reprise dans ce champ.

`4)` Si le point de contact est généré à partir d’une campagne CRM, cette information est reprise dans ce champ.

`5)` Si le point de contact est généré à partir d’une activité CRM, cette information est reprise dans ce champ.

Si aucun des scénarios ci-dessous ne s’applique, ce champ recevra la valeur « Web Direct » ou « Web ».

**Source du point de contact (FT)** | Point de contact acheteur

Il s’agit du même champ que « Source du point de contact », mais il indique spécifiquement la source du premier point de contact.

**Source du point de contact (LC)** | Point de contact acheteur

Il s’agit du même champ que « Source du point de contact », mais il indique spécifiquement la source ayant permis la création du prospect.

**Type de point de contact** | Correspond aux points de contact acheteur et aux points de contact d’attribution acheteur

Ce champ affiche le type d’interaction du point de contact : visite web, formulaire web ou messagerie instantanée web pour les points de contact JavaScript. Pour les points de contact correspondant à des campagnes CRM, la valeur « CRM » est indiquée. Pour les points de contact d’activité, la tâche ou le type d’événement est indiqué.

[Cliquez ici pour revenir en haut de la page.](#top)

U

**Identifiant unique** | Point de contact acheteur, point de contact d’attribution acheteur

Identifiant unique associé à chaque point de contact.

**Identifiant utilisateur** | Test A/B Marketo Measure

Code d’identification unique Optimizely pour chaque utilisation.

[Cliquez ici pour revenir en haut de la page.](#top)

## V {#v}

**Variation** | Test A/B Marketo Measure

Nom de la variation du test A/B.

**Identifiant de variation** | Test A/B Marketo Measure

Code d’identification unique de chaque variation d’un test A/B.

[Cliquez ici pour revenir en haut de la page.](#top)
