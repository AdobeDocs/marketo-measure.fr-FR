---
unique-page-id: 18874596
description: Configuration de canal personnalisé en ligne - [!DNL Marketo Measure]
title: Configuration de canal personnalisé en ligne
exl-id: 170ac564-6cdd-4036-abf0-b9b230bed4f7
feature: Channels
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 71%

---

# Configuration de canal personnalisé en ligne {#online-custom-channel-setup}

Pour des rapports précis, les canaux marketing doivent être configurés pour refléter la stratégie de gestion dynamique des balises de votre entreprise. Ce guide vous explique comment configurer au mieux vos règles de canal personnalisées.

## Avant de commencer {#before-you-begin}

Avant de commencer à créer vos règles de canal pour [!DNL Marketo Measure], prenez le temps de réfléchir à l’organisation de vos campagnes marketing et à leur place dans la structure de [!DNL Marketo Measure]. Déterminez les canaux, sous-canaux, campagnes et sites web référents dont vous souhaitez effectuer le suivi.

Points à retenir :

* Votre entreprise peut créer un maximum de 40 canaux marketing personnalisés. Cela inclut les canaux hors ligne et en ligne.
* Votre entreprise peut créer jusqu’à 200 sous-canaux.
* Chaque collection (ou compartiment) de données doit disposer de sa propre règle (ligne dans la feuille de calcul) pour spécifier la manière dont les données seront organisées. Soyez aussi précis que possible.
* La logique [!DNL Marketo Measure] donne la priorité aux données dans l’ordre décroissant, en commençant par la ligne supérieure de la feuille de calcul et en descendant. Chaque compartiment, ou cellule, est lu ligne par ligne à la recherche de la première correspondance. Les données sont ensuite triées en fonction des valeurs contenues dans ces compartiments. Plus d’informations à ce sujet ci-dessous.
* Ne triez pas votre feuille dans l’ordre alphabétique, car cela interfère avec les règles logiques.
* Une fois le fichier chargé, vous ne pouvez plus modifier les règles pendant sept jours. Pendant cette période, [!DNL Marketo Measure] traite et met à jour les points de contact.

## Logique et priorités dans [!DNL Marketo Measure] {#marketo-measure-logic-and-priorities}

La première étape consiste à télécharger la feuille de calcul de canal personnalisé dans l’application [!DNL Marketo Measure]. Accédez aux **Paramètres** sous l’onglet **Mon compte**, puis sélectionnez **En ligne**. Vous pouvez **télécharger le modèle d’origine** ou **télécharger les règles actuelles**.

![](assets/1.png)

La feuille de calcul comporte sept colonnes :

![](assets/2.png)

* **Canal :** c’est ici que vous ajoutez les différents canaux marketing.
* **Sous-canal :** c’est ici que vous ajoutez les sous-canaux correspondants.
* **Campagne :** ajoutez des noms de campagne ici, que la valeur provienne des UTM ou des campagnes Salesforce pour la variable [!DNL Marketo Measure] Fonctionnalité des activités
* **Support :** cette colonne reprend la valeur du paramètre utm_medium.
* **Source :** cette colonne reprend la valeur du paramètre utm_source.
* **Page de destination :** ajoutez ici la page de destination.
* **Site web de renvoi :** il s’agit des URL des sites web qui renvoient du trafic vers vos pages ou vers la logique [!DNL Marketo Measure] (indiquée par crochets).

La huitième colonne indique les règles que vous ne pouvez pas supprimer de la feuille de calcul avec le message &quot;Ne pas supprimer&quot;. Le haut de la feuille de calcul comporte des règles de canal par défaut. [!DNL Marketo Measure] recommande de ne pas les modifier ni les supprimer, même si vous ne les utilisez pas. [!DNL Marketo Measure] dispose d’intégrations performantes avec ces plateformes, elles sont donc incluses par défaut.

Les lignes représentent les règles et l’ordre dans lequel [!DNL Marketo Measure] donne la priorité aux données. La première ligne est prioritaire par rapport à la seconde, la deuxième ligne l’est par rapport à la troisième, etc. Lorsque vous déterminez le canal marketing et le sous-canal dans lequel regrouper les points de contact, [!DNL Marketo Measure] lance une lecture de haut en bas, de gauche à droite, jusqu’à ce qu’elle trouve une ligne qui répond aux critères du point de contact. (Si un point de contact comporte une `utm_source=Facebook`, le point de contact est regroupé dans le canal Social.Facebook en raison de la règle 15 de la capture d’écran).

![](assets/3.png)

[!DNL Marketo Measure] est fourni avec 12 canaux par défaut, liés à des plateformes avec lesquelles [!DNL Marketo Measure] dispose d’intégrations complètes. Que vous les utilisiez ou non, ne les supprimez pas. Si vous utilisez l’une de ces plateformes, par exemple Bing Ads, mais que vous préférez utiliser une convention de nommage différente pour le canal ou le sous-canal, vous pouvez mettre à jour le nom. L’image ci-dessous présente un exemple.

![](assets/4.png)

La structure des règles est également importante. Des règles peuvent sembler se répéter et vous pouvez avoir l’impression que des données sont manquantes, mais cette structure est intentionnelle. Pour trier les données de façon précise, il est nécessaire de mapper séparément chaque source au canal approprié, y compris pour les sources partageant des sous-canaux et des canaux. Plus les règles sont détaillées et granulaires, plus les résultats sont pertinents. En gros, il est recommandé d’écrire une règle détaillée pour chaque effort marketing dont vous souhaitez effectuer le suivi.

Imaginez la situation suivante : vous avez d’autres publicités dont vous ne souhaitez pas effectuer le suivi pour une raison quelconque, ou vous recevez des visites sur votre site web à partir d’un canal habituel, mais qui ne correspond pas à une source habituelle. Cette situation peut entraîner une perte de données si [!DNL Marketo Measure] ne trouve pas la règle appropriée à utiliser pour trier les données. Pour empêcher cela, [!DNL Marketo Measure] vous conseille de répartir la règle sur plusieurs lignes.

Chaque paramètre ou composant de la règle est mappé séparément au canal. Par exemple, lorsque [!DNL Marketo Measure] dispose de données [!DNL Facebook] à trier, il recherche des règles liées à [!DNL Facebook]. Il scanne alors la feuille de haut en bas. Dans l’exemple illustré ci-dessous, [!DNL Marketo Measure] comprendrait que pour le premier sous-canal [!DNL Facebook], il lui suffit de lire le paramètre de source et de déposer les données dans le compartiment de cette règle.

![](assets/5.png)

La règle suivante ne demande que le paramètre medium. Par conséquent, toutes les données comportant ce paramètre sont regroupées dans ce canal. Enfin pour [!DNL Facebook], toutes les données provenant de l’URL Facebook sont placées dans le dernier compartiment Facebook.

Le canal par défaut « Autre » permet de capturer des données qui ne répondent aux critères d’aucune règle. Notez que certains des compartiments du canal Autre contiennent des astérisques (&#42;), qui représentent des caractères génériques et qui agissent donc comme un fourre-tout.

![](assets/6.png)

En raison de [!DNL Marketo Measure] logique fonctionnant de haut en bas, la règle de caractère générique, indiquée par un astérisque (&#42;), doit être placé à la fin de votre feuille de règles. Toutes les données qui ne sont pas capturées ou triées par les autres règles sont ajoutées à ce compartiment de caractères génériques.

Vous trouverez ci-dessous d’autres exemples de logique avec des caractères génériques :

* &#42;email&#42; = contient « email »
* &#42;email = se termine par « email »
* email&#42; = [!UICONTROL commence par « email »]

En outre, si vous créez un sous-canal pour l’un de vos canaux, vous devez créer un sous-canal pour toutes les règles sous ce canal. En d’autres termes, si vous créez un sous-canal, vous ne pouvez pas laisser le reste des colonnes vides.

## Configuration de règles de canaux personnalisés {#setting-up-your-custom-channels-rules}

Une fois que vous avez décidé comment organiser et prioriser vos données, vous pouvez ajouter vos règles à la feuille de calcul. Voici quelques bonnes pratiques :

* Faites en sorte que vos règles soient aussi simples que possible dès le départ. Vous pouvez toujours ajouter de la complexité au fur et à mesure.
* N’ajoutez pas de caractères spéciaux dans les noms de canal (par exemple, $%#&amp;&#42;@)
* Ne modifiez pas les règles associées à Bing Ads ou à AdWords. Elles sont essentielles au regroupement automatique des données issues de l’API d’intégration [!DNL Marketo Measure] avec ces plateformes. Toutefois, vous pouvez modifier le nom du sous-canal et du canal.
* Ne supprimez pas les règles contenant une note « Ne pas supprimer ».
* Les règles de référencement naturel sont toujours placées après les [!UICONTROL règles de référencement payant].
* Vous ne pouvez pas créer de règles basées sur différents sous-domaines.
* Si vous devez indiquer plusieurs valeurs dans une seule cellule de la feuille de calcul, séparez-les par des points-virgules (`;`) uniquement. N’utilisez pas de virgules ni d’espaces.
* Il n’est pas nécessaire d’ajouter dot-com (.com) à la fin de l’URL de référence.
* Lors de l’ajout d’une URL de référence, ne la placez pas entre crochets comme les autres règles liées aux API.

## Chargement de vos règles de canaux personnalisés {#uploading-your-custom-channels-rules}

Assurez-vous que toutes les nouvelles valeurs de canal et de sous-canal que vous ajoutez dans le fichier CSV ont déjà été ajoutées dans la zone des paramètres de canal de votre compte Bizible. Vérifiez bien que tous les noms de canal et de sous-canal dans le fichier CSV correspondent aux paramètres de canal de votre compte [!DNL Marketo Measure]. Veillez à ne pas laisser de virgules ni d’espaces.

Si vous recevez un message d’erreur lors du téléchargement, corrigez le problème et rechargez. Si aucun message d’erreur n’apparaît, cliquez sur **Confirmer et traiter** au bas de la page.
