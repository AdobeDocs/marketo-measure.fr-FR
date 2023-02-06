---
unique-page-id: 18874586
description: Glossaire des champs Marketo Measure - Marketo Measure - Documentation du produit
title: Glossaire des champs Marketo Measure
exl-id: 8e23b102-6d4f-4919-b361-04d1b184e710
source-git-commit: 334dcd3dcbddacc4920d182d94908babd3cb8c89
workflow-type: tm+mt
source-wordcount: '3211'
ht-degree: 0%

---

# Glossaire des champs Marketo Measure {#glossary-of-marketo-measure-fields}

Cet article fournit un glossaire de tous les champs Marketo Measure ajoutés à votre Salesforce à partir du package de base Marketo Measure. Vous trouverez également des informations sur l’objet sur lequel le champ se trouve et sur la manière dont chaque champ est renseigné.

Pour une carte de l’objet auquel chaque champ Marketo Measure se rapporte, veuillez [cliquez ici](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

[A](#a) ・ [B](#b) ・ [C](#c) ・ [D](#d) ・ [E](#e) ・ [F](#f) ・ [G](#g) ・ H ・ I ・ J [k](#k) ・ [L](#l) ・ [M](#m) ・ N [O](#o) ・ [P](#p) ・ Q [R](#r) ・ [s](#s) ・ [T](#t) ・ [U](#u) ・ [V](#v) ・ W ・ X ・ Y

## R {#a}

**Compte** | Trouvé sur le point de contact d’attribution de l’achat

Ce champ est renseigné avec le nom du compte associé à la taxe aux conditions préalables à l’expiration.

**Identifiant de campagne publicitaire** | Trouvé sur le point de contact de l’achat, point de contact de l’attribution de l’achat

Ce champ peut être renseigné de trois façons :

`1)` Si le point de contact provient d’un effort de recherche payante (AdWords ou BingAds), l’identifiant de campagne publicitaire de la plateforme publicitaire est affiché ici.

`2)` Si le point de contact ne provient pas de la recherche payante, le champ est renseigné à l’aide de la valeur utm_campaign de l’URL de la page d’entrée.

par ex., `http://info.marketomeasure.com/adwords-for-lead-generation?utm_source=Event&utm_medium=booth&utm_campaign=Marketo%20Virtual%20Event%20sep2014`

Dans cet exemple, l’identifiant de campagne publicitaire affiche : __GAId__ Événement virtuel marketing sept-2014

`3)` Si le point de contact provient d’une campagne Salesforce hors ligne (une conférence, un dîner, etc.), l’identifiant de campagne publicitaire apparaîtra sur l’identifiant de campagne Salesforce.

Si aucun des champs ci-dessus n’est spécifié, ce champ sera vide.

**Nom de la campagne publicitaire** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante (AdWords/Bing Ads), le nom de la campagne publicitaire de la plateforme publicitaire s’affiche ici.

`2)` Si le point de contact ne provient pas de la recherche payante et que l’URL de la page d’entrée contient une valeur pour utm_campaign, cette valeur est renseignée ici.

`3)` Si le point de contact provient d’une campagne Salesforce, le nom de la campagne Salesforce s’affiche ici.

`4)` Cela renseigne le nom de campagne défini pour les points de contact générés à partir des activités, comme créé dans votre compte Marketo Measure.

Si aucun des champs ci-dessus n’est spécifié, ce champ sera vide.

**Nom de la campagne publicitaire (FT)** | Point de contact de l’achat

Ce champ est renseigné de la même manière que le Nom de la campagne publicitaire. Cependant, ce champ vous indique spécifiquement le nom de la campagne publicitaire qui a généré le point de contact Première touche.

**Nom de la campagne publicitaire (LC)** | Point de contact de l’achat

Ce champ est renseigné de la même manière que le Nom de la campagne publicitaire. Cependant, ce champ indique spécifiquement le nom de la campagne publicitaire qui a généré le point de contact de la création de piste.

**Contenu de la publicité** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante (AdWords/Bing Ads), le champ affiche la copie complète de la publicité depuis la plateforme.

`2)` Si le point de contact ne provient pas d’une recherche payante, ce champ affiche la valeur utm_content dans l’URL de la page d’entrée.

`3)` Cela renseignera avec la valeur Objet de l’activité associée qui a généré le point de contact.

Si aucun des champs ci-dessus n’est renseigné, ce champ sera vide.

**URL de destination de l’annonce** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante, ce champ affiche la destination de l’URL à laquelle vous êtes dirigé après avoir cliqué sur la publicité dans le moteur de recherche.

Si le point de contact ne provient pas d’une recherche payante, le champ est vide.

**Identifiant du groupe publicitaire** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante, l’identifiant du groupe publicitaire AdWords/Bing Ads s’affiche ici.

Si le point de contact ne provient pas de la recherche payante, le champ est vide.

**Nom du groupe publicitaire** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante, le nom du groupe d’annonces AdWords/Bing Ads s’affiche ici.

Si le point de contact ne provient pas de la recherche payante, le champ est vide.

**Identifiant de publicité** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante, l’ID de publicité d’AdWords/Bing Ads s’affiche ici.

`2)` Cela sera renseigné avec l’ID externe Activité si le point de contact est généré à partir d’une activité CRM.

Si le point de contact ne provient pas de la recherche payante, le champ est vide.

**Attribution % Modèle personnalisé** | Point de contact d’attribution de l’achat

Si vous utilisez un modèle d’attribution personnalisé, ce champ affiche le pourcentage des recettes attribuées à un point de contact en fonction des valeurs définies dans votre modèle personnalisé.

Si vous n’utilisez pas de modèle personnalisé, ce champ sera vide.

**Attribution % Première touche** | Point de contact d’attribution de l’achat

Ce champ affiche le pourcentage des recettes attribuées à un point de contact en fonction d’un modèle Première touche.

**Attribution % Complet** | Point de contact d’attribution de l’achat

Ce champ affiche le pourcentage des recettes attribuées à un point de contact en fonction d’un modèle de chemin complet.

**Attribution % Création de piste** | Point de contact d’attribution de l’achat

Ce champ affiche le pourcentage des recettes attribuées à un point de contact, selon un modèle de création de piste.

**Attribution % en forme de U** | Point de contact d’attribution de l’achat

Ce champ affiche le pourcentage des recettes attribuées à un point de contact en fonction d’un modèle en forme de U.

**Attribution % en forme W** | Point de contact d’attribution de l’achat

Ce champ affiche le pourcentage des recettes attribuées à un point de contact selon un modèle en forme de W.

[Cliquez ici pour revenir en haut de la page](#top)

## B {#b}

**Montant de l’opportunité Marketo Measure** | Opportunité Salesforce

Si vous utilisez un champ Montant personnalisé pour signaler les recettes d’opportunité, Marketo Measure ne peut pas lire ces champs Montant personnalisé. Le montant de l’opportunité Marketo Measure est un champ masqué qui est utilisé pour créer un workflow qui permet à Marketo Measure de lire les champs de montant personnalisés sur l’opportunité.

**Navigateur** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche le type de navigateur Web utilisé au cours de la session Web (Chrome, Safari, Firefox, etc.).

[Cliquez ici pour revenir en haut de la page](#top)

## C {#c}

**Contact** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Le champ affiche le contact auquel le point de contact appartient.

**Count - Modèle personnalisé** | Point de contact d’attribution de l’achat

Si vous utilisez un modèle d’attribution personnalisé, ce champ affiche, sous forme décimale, le pourcentage du crédit de recettes attribué à un point de contact en fonction des valeurs définies dans votre modèle personnalisé.

Si vous n’utilisez pas de modèle personnalisé, ce champ sera vide.

**Count - Modèle personnalisé** | Point de contact de l’achat

Si vous utilisez un modèle d’attribution personnalisé, ce champ affiche, sous forme décimale, le pourcentage du crédit d’attribution accordé à un point de contact en fonction des valeurs définies dans votre modèle personnalisé. Puisque ce champ se rapporte à l’objet point de contact de l’acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

Si vous n’utilisez pas de modèle personnalisé, ce champ sera vide.

**Nombre - Première touche** | Point de contact d’attribution de l’achat

Ce champ affiche, sous forme décimale, le pourcentage du crédit de recettes attribué à un point de contact selon un modèle Première touche.

**Nombre - Première touche** | Point de contact de l’achat

Ce champ affiche, sous forme décimale, le pourcentage du crédit d’attribution attribué à un point de contact selon un modèle Première touche. Si le point de contact est Première touche, ce champ sera toujours de 1,0 (ce qui indique un crédit d’attribution à 100 %). Si le point de contact n’est pas la Première touche, ce champ sera toujours 0 (indiquant 0 % de crédit d’attribution).

Puisque ce champ se rapporte à l’objet point de contact de l’acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

**Nombre - Chemin complet** | Point de contact d’attribution de l’achat

Ce champ affiche, sous forme décimale, le pourcentage des recettes données à un point de contact selon un modèle de chemin complet.

**Comptage - Contact de création de piste** | Point de contact d’attribution de l’achat

Ce champ affiche, sous forme décimale, le pourcentage du crédit de recettes attribué à un point de contact selon un modèle de création de piste.

**Comptage - Contact de création de piste** | Point de contact de l’achat

Ce champ affiche, sous forme décimale, le pourcentage du crédit d’attribution attribué à un point de contact selon un modèle de création de piste. Si le point de contact est la touche Création de piste , ce champ sera toujours de 1,0 (ce qui indique un crédit d’attribution à 100 %). Si le point de contact n’est pas la touche Création de piste, ce champ sera toujours de 0 (ce qui indique un crédit d’attribution de 0 %).

Puisque ce champ se rapporte à l’objet point de contact de l’acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

**Count - En forme de U** | Point de contact d’attribution de l’achat

Ce champ affiche, sous forme décimale, le pourcentage du crédit de recettes attribué à un point de contact selon un modèle en forme de U.

**Count - En forme de U** | Point de contact de l’achat

Ce champ affiche, sous forme décimale, le pourcentage du crédit d’attribution attribué à un point de contact selon un modèle en forme de U. Dans le modèle en forme de U, le crédit est divisé entre la Première touche, la Touche de création de piste et toutes les soumissions de formulaires intermédiaires qui se sont produites entre la Première touche et la Touche de création de piste.

Puisque ce champ se rapporte à l’objet point de contact de l’acheteur, il ne reflète pas un crédit de revenu, mais uniquement un crédit d’attribution.

**Count - En forme de W** | Point de contact d’attribution de l’achat

Ce champ affiche, sous forme décimale, le pourcentage du crédit accordé à un point de contact selon un modèle en forme de W.

[Cliquez ici pour revenir en haut de la page](#top)

## D {#d}

Date de rapport | Marketo Measure ABTest, événement Marketo Measure

Événement Marketo Measure : date à laquelle un utilisateur a effectué une action spécifique sur votre site web, en activant un événement.

Marketo Measure ABTest : date à laquelle un utilisateur a participé à un test A/B sur votre site web.

[Cliquez ici pour revenir en haut de la page](#top)

## E {#e}

**Nom de l’événement** | Événement Marketo Measure

Ce champ affiche le nom de l’action qui a déclenché l’événement (c.-à-d. Page vue).

**Valeur d’événement** | Événement Marketo Measure

La description de l’événement (c’est-à-dire la page d’accueil)

**Nom de l’expérience** | Marketo Measure ABTest

Ce champ affiche le nom de l’expérience (c.-à-d. Bouton Évaluation).

**Identifiant de l’expérience** |Test AB Marketo Measure

Le code d’identification unique de chaque expérience

[Cliquez ici pour revenir en haut de la page](#top)

## F {#f}

URL du formulaire | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche une version abrégée de l’URL d’une page où le remplissage du formulaire s’est produit (aucun paramètre UTM).

URL du formulaire - Brut | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche l’URL de la page entière où le remplissage du formulaire s’est produit, y compris les paramètres UTM.

[Cliquez ici pour revenir en haut de la page](#top)

## G {#g}

Geo City | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ indique le nom de la ville dans laquelle le prospect/contact a consulté votre site web. Cette opération s’effectue par le biais de la recherche d’adresses IP inversées.

Geo Country | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ indique l’endroit où le prospect/contact a consulté votre site web. Cette opération s’effectue par le biais de la recherche d’adresses IP inversées.

Région géographique | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ indique la région ou l’état dans lequel le prospect/contact a consulté votre site web. Cette opération s’effectue par le biais de la recherche d’adresses IP inversées.

[Cliquez ici pour revenir en haut de la page](#top)

## k {#k}

**Identifiant du mot-clé** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Si le point de contact provient d’une recherche payante, ce champ affiche l’identifiant du mot-clé de la plateforme publicitaire (AdWords/BingAds).

Si ce point de contact n’est pas issu d’une recherche payante, ce champ est vide.

**Type de correspondance de mot-clé** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Si le point de contact provient d’une recherche payante, ce champ affiche le type de correspondance de la plateforme publicitaire (AdWords/Bing).

**Texte du mot-clé** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante, ce champ affiche le texte du mot-clé de la plateforme publicitaire (Adwords/BingAds) OU la valeur du paramètre _bk dans l’URL de la page d’entrée.

par ex., `http://info.marketomeasure.com/intro-guide-b2b-marketing-attribution?_bt=12345678&_bk=marketing%20attribution&_bm=p&gclid=ABc123def456ghi789jkl`

`2)` Si le point de contact ne provient pas de la recherche payante, ce champ affiche la valeur utm_term de l’URL de la page d’entrée.

`http://www.marketomeasure.com/blog/lead-generation?utm_source=linkedin&utm_medium=Social&utm_campaign=ABC%20Blog&utm_content=Lead%20Gen&utm_term=lead%20gen`.

Si le point de contact ne provient pas d’une recherche payante ou s’il n’existe aucune valeur utm_term, ce champ sera vide.

[Cliquez ici pour revenir en haut de la page](#top)

## P {#l}

**Page d’entrée** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche la version abrégée de l’URL (aucun paramètre UTM) de la première page web visitée lors d’une session web.

**Page d’entrée - Raw** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche l’URL complète (y compris les paramètres UTM) de la première page web visitée au cours d’une session web.

**prospect** | Point de contact de l’achat, personne Marketo Measure

Ce champ affiche le nom de la piste à laquelle appartient un point de contact.

[Cliquez ici pour revenir en haut de la page](#top)

## M {#m}

**Canal marketing** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ vous présente le groupe général d’activités marketing ou de canaux marketing auquel le point de contact appartient (c’est-à-dire Recherche payante, Direct, Social, etc.). Les points de contact sont regroupés en fonction de la configuration de vos canaux dans l’application Marketo Measure. Pour plus d’informations sur les canaux marketing ou sur la configuration de vos canaux, veuillez [cliquez ici](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

**Canal marketing - Chemin** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ vous présente le canal marketing et le sous-canal auquel appartient un point de contact. Dans l’exemple ci-dessous, Canal marketing - Chemin est Social.Linkedin, où le canal marketing est Social, et le sous-canal est LinkedIn.

![](assets/1-3.png)

**Volume moyen** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante, le support provenant d’AdWords/BingAds s’affiche ici (c.-à-d. CPC).

`2)` Si le point de contact ne provient pas de la recherche payante, ce champ affiche la valeur utm_medium de l’URL de la page d’entrée.

`3)` Si le point de contact provient d’une campagne hors ligne, ce champ affiche le champ &quot;Type&quot; dans la campagne Salesforce.

`4)` Cette valeur est renseignée avec la valeur Type d’activité de l’activité associée qui a généré le point de contact.

Si aucune des valeurs ci-dessus n’est définie, Marketo Measure définit automatiquement une valeur moyenne.

[Cliquez ici pour revenir en haut de la page](#top)

O

**Opportunité** | Point de contact d’attribution de l’achat

Ce champ affiche l’opportunité à laquelle le AT appartient.

[Cliquez ici pour revenir en haut de la page](#top)

P

**Plateforme** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche le type d’ordinateur ou de téléphone et le type de système d’exploitation utilisé au cours de la session web.

[Cliquez ici pour revenir en haut de la page](#top)

R

**Page du référent** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche l’URL (sans paramètres UTM) de la dernière page web sur laquelle se trouvait le prospect/contact qui les a dirigés vers votre site web.

Par exemple :

- Si le point de contact provient d’une recherche payante/organique, le champ indique l’URL du moteur de recherche.

- Si le point de contact provient de Social, le champ indique l’URL du site Web social (c’est-à-dire LinkedIn).

**Page du référent - Brut** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche les mêmes informations que la page du référent, à la différence que ce champ affiche l’URL de référence entière (y compris les paramètres UTM).

**Recettes - Modèle personnalisé** | Point de contact d’attribution de l’achat

Si vous utilisez un modèle d’attribution personnalisé, ce champ indique le montant des recettes en dollars attribué à un point de contact en fonction du pourcentage d’attribution défini dans votre modèle personnalisé.

Si vous n’utilisez pas de modèle personnalisé, le montant en dollars sera 0.

**Recettes - Première touche** | Point de contact d’attribution de l’achat

Ce champ affiche le montant des recettes en dollars attribué à un point de contact en fonction du pourcentage d’attribution dans le modèle Première touche.

**Recettes - Chemin complet** | Point de contact d’attribution de l’achat

Ce champ affiche le montant des recettes en dollars attribué à un point de contact en fonction du pourcentage d’attribution dans le modèle de chemin complet.

**Recettes - Tactile de création de pistes** | Point de contact d’attribution de l’achat

Ce champ indique le montant des recettes en dollars attribué à un point de contact en fonction du pourcentage d’attribution dans le modèle de création de piste.

**Recettes - En forme de U** | Point de contact d’attribution de l’achat

Ce champ affiche le montant des recettes en dollars attribué à un point de contact en fonction du pourcentage d’attribution dans le modèle en forme de U.

**Recettes - En forme de W** | Point de contact d’attribution de l’achat

Ce champ affiche le montant des recettes en dollars attribué à un point de contact en fonction du pourcentage d’attribution dans le modèle en forme de W.

[Cliquez ici pour revenir en haut de la page](#top)

Sam.

**Campagne Salesforce** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche la campagne Salesforce à laquelle le point de contact appartient.

**Expression de recherche** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Si le point de contact provient du référencement payant ou organique, ce champ affiche l’expression de recherche saisie dans le moteur de recherche. Cependant, pour des raisons de confidentialité, ces informations ne sont généralement pas disponibles.

**Segment** | Point de contact d’attribution de l’achat

Ce champ affiche les segments auxquels le point de contact appartient. Cela dépendra de la manière dont vous avez configuré vos règles de segmentation dans l’application Marketo Measure.

[Cliquez ici pour revenir en haut de la page](#top)

Ma.

**Date du point de contact** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une source en ligne, ce champ affiche la date et l’heure auxquelles le point de contact s’est produit.

`2)` Si le point de contact provient d’un événement hors ligne, ce champ affiche la date et l’heure définies dans la campagne Salesforce ou à partir du champ de date sélectionné dans les règles de synchronisation de campagne.

`3)` Si le point de contact provient d’une activité, ce champ affiche la date et l’heure du champ sélectionné comme Date du point de contact dans les règles d’activité.

**Date du point de contact (FT)** | Point de contact de l’achat

Il s’agit du même champ que Date du point de contact. Toutefois, ce champ affiche spécifiquement la date et l’heure auxquelles le point de contact Première touche s’est produit.

**Date du point de contact (LC)** | Point de contact de l’achat

Il s’agit du même champ que la Date du point de contact. Toutefois, ce champ affiche spécifiquement la date et l’heure auxquelles le point de contact de la création de piste a eu lieu.

**Position du point de contact** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Ce champ affiche la position du point de contact. La position du point de contact reflète les principaux points de contact de jalon dans le parcours client (c’est-à-dire FT, Form, LC, OC, Fermé). La position du point de contact dépend du moment où il s’est produit dans le parcours client et un seul point de contact peut avoir plusieurs positions. Les différentes positions des points de contact sont les suivantes :

Première touche (FT) - La toute première interaction marketing qu’une personne a avec votre marque

Création de piste (LC) : toute première interaction marketing connue (généralement un envoi de formulaire ou une inclusion de campagne Salesforce).

Formulaire : lorsqu’un visiteur remplit un formulaire en ligne

Création d’opportunité (OC) : interaction marketing la plus proche du moment où l’Opp est créée

Fermé : interaction marketing la plus proche de la fermeture de l’Opp (Gagnant ou perdu).

**Source du point de contact** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

`1)` Si le point de contact provient d’une recherche payante, ce champ affiche le nom de la plateforme publicitaire (AdWords/BingAds).

`2)` Si le point de contact provient de la recherche organique, ce champ affiche le nom du moteur de recherche.

`3)` Si elle n’est pas #1 ou #2 et que la valeur utm_source est présente dans l’URL de la page d’entrée pour le point de contact, cette valeur est affichée ici.

`4)` Cela sera renseigné en tant que campagne CRM si le point de contact est généré à partir d&#39;une campagne CRM.

`5)` Cela sera renseigné en tant qu’activité CRM si le point de contact est généré à partir d’une activité CRM.

Si aucun des champs ci-dessus n’est renseigné, ce champ sera &quot;Web Direct&quot; ou &quot;Web&quot;.

**Source du point de contact (FT)** | Point de contact de l’achat

Il s’agit du même champ que la source du point de contact. Toutefois, ce champ affiche spécifiquement la source du point de contact Première touche.

**Source du point de contact (LC)** | Point de contact de l’achat

Il s’agit du même champ que la source du point de contact. Toutefois, ce champ affiche spécifiquement la source du point de contact de la création de piste.

**Type de point de contact** | Situé sur le point de contact de l’achat et le point de contact de l’attribution de l’achat.

Ce champ affiche le type d’interaction du point de contact. Il s’affichera comme suit : Visite web, formulaire web ou conversation web pour les points de contact JavaScript. Pour les points de contact CRM Campaign, il s&#39;affichera sous forme de CRM. Il sera renseigné avec la tâche ou le type d’événement pour les points de contact d’activité.

[Cliquez ici pour revenir en haut de la page](#top)

U

**UniqueId** | Point de contact de l’acheteur, point de contact de l’attribution de l’acheteur

Identifiant unique associé à chaque point de contact.

**Identifiant utilisateur** | Marketo Measure ABTest

Code d’identification unique d’Optimizely pour chaque utilisation

[Cliquez ici pour revenir en haut de la page](#top)

## V {#v}

**Variation** | Marketo Measure ABTest

Nom de la variation du test A/B.

**ID de variation** | Marketo Measure ABTest

Code d’identification unique pour chaque variante de test A/B.

[Cliquez ici pour revenir en haut de la page](#top)
