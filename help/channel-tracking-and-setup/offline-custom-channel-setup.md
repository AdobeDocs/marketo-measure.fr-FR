---
description: Conseils de configuration de canal personnalisé hors ligne pour les utilisateurs de Marketo Measure
title: Configuration de canal personnalisé hors ligne
exl-id: c5697714-1a79-40bd-8b7c-e10768f4ef67
feature: Channels
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 1%

---

# Configuration de canal personnalisé hors ligne {#offline-custom-channel-setup}

## Prise en main {#getting-started}

Par rapport à la façon dont [!DNL Marketo Measure] gère les règles de canal en ligne, vous remarquerez que les règles de canal hors ligne ne nécessitent pas l’utilisation d’une feuille de calcul. Cependant, une feuille est toujours fournie dans le plan de mise en œuvre, car cela peut s’avérer utile pour réfléchir à la manière dont vous souhaitez organiser vos canaux hors ligne.

La feuille de calcul comporte trois colonnes :

![La feuille de calcul comporte trois colonnes :](assets/offline-channels-1.png)

**[!UICONTROL Salesforce ] type de campagne** - ajoutez les types de campagne identifiés dans [!DNL Salesforce] ici

* Il peut s’agir, par exemple, d’un e-mail, d’un webinaire, d’une conférence ou de toute autre valeur que vous avez créée pour ce champ auquel vous souhaitez attribuer des points de contact.

**[!UICONTROL Canal]** - ajoutez vos différents canaux marketing ici

**[!UICONTROL Sous-canal]** - ajoutez tous les sous-canaux correspondants ici

## Logique de canal hors ligne {#offline-channel-logic}

[!DNL Marketo Measure] logique de canal hors ligne est déterminée par l’objet Campaign, en particulier le type de campagne [!DNL Salesforce]. Chaque effort hors ligne doit avoir un type de campagne [!DNL Salesforce], tel que dîner ou salon, car [!DNL Marketo Measure] s’appuie sur ce champ pour comprendre le canal et le sous-canal à mapper.

Les types de campagne SFDC apparaissent dans l’onglet Canal hors ligne , répertoriés sous Type de campagne [!DNL Salesforce]. Notez que [!DNL Marketo Measure] ne peut importer des types de campagne SFDC que pour les campagnes auxquelles des points de contact Acheteur sont associés.

![Les types de campagne SFDC apparaissent dans l’onglet Canal hors ligne , répertoriés](assets/offline-channels-10.jpg)

C’est là que vous pouvez créer le mappage Canal/Sous-canal dans l’application [!DNL Marketo Measure]. Cela impliquera probablement la création de nouveaux canaux et sous-canaux dans l’application [!DNL Marketo Measure], ce qui est fait dans la section Créer des canaux de l’application, comme illustré dans l’image ci-dessous. De nouveaux canaux et sous-canaux doivent être créés pour que les [!DNL Marketo Measure] puissent comprendre où transmettre les points de contact. Vous pouvez décider de la manière dont vous souhaitez mapper les types de campagne.

![C’est là que vous pouvez créer le mappage Canal/Sous-canal dans le ](assets/offline-channels-11.png)

## Exemple de mappage de canal {#channel-mapping-example}

Imaginez, par exemple, que vous assistiez à deux conférences [!DNL Salesforce] par an. Cependant, chaque conférence est très différente et a un public cible unique. Vous voulez savoir lequel des deux apporte le plus de valeur. Dans votre environnement [!DNL Salesforce], vous pouvez donner à l’événement de janvier le type de campagne « Conférence », nommer votre canal « [!DNL Salesforce] » et votre sous-canal « Conférence de janvier ».

Maintenant, vous voulez faire la même chose pour la conférence de juin. Vous pensez que puisqu’il s’agit également d’une conférence, elle peut recevoir le même type de campagne, dans ce cas « Conférence ». Le canal est le même, [!DNL Salesforce], et le sous-canal pour cette deuxième conférence est « Conférence de juin ». D&#39;un point de vue organisationnel, c&#39;est logique. Toutefois, il est très déroutant pour la logique [!DNL Marketo Measure] de lire et d’appliquer ces règles, car les deux campagnes ont le même type de campagne. [!DNL Marketo Measure] script ne peut pas mapper les données d’un type à deux sous-canaux différents. Cela signifie que vous devez créer un nouveau type de campagne pour chaque sous-canal, mais les sous-canaux peuvent avoir le même canal.

Voici un exemple de logique que [!DNL Marketo Measure] ne pourriez pas lire :

![Vous trouverez ci-dessous un exemple de logique que Marketo Measure n’accepterait pas](assets/offline-channels-12.png)

Dans le scénario ci-dessus, vous souhaiterez créer un type de campagne unique, car vous ne pouvez pas mapper le même type de campagne à deux sous-canaux différents. À la place, vous pouvez configurer des types uniques comme ceux-ci :

![Dans le scénario ci-dessus, vous souhaiterez créer une campagne unique](assets/offline-channels-13.png)

Tous les types de campagne existants doivent être inclus dans votre mappage de canal et la valeur « NULL » doit être ajoutée comme canal.

Prenez le temps de consulter [!DNL Salesforce] pour déterminer le nombre et la nature des types d’enregistrements existants que vous souhaitez inclure et si vous devez créer des campagnes supplémentaires en fonction des informations ci-dessus. Une fois que vous avez renseigné toutes les informations nécessaires, vous êtes prêt à effectuer le chargement.

En savoir plus sur la [synchronisation des campagnes hors ligne [!DNL Salesforce] avec [!DNL Marketo Measure]](/help/channel-tracking-and-setup/syncing-offline-campaigns.md).

## Gestion des campagnes SFDC pour les efforts de marketing en ligne {#handling-sfdc-campaigns-for-online-marketing-efforts}

Il est courant que les équipes marketing créent des campagnes [!DNL Salesforce] pour suivre divers efforts de marketing numérique. Cette pratique ne pose aucun problème. Cependant, il est important de traiter ces campagnes différemment des véritables campagnes hors ligne, telles que le publipostage direct ou les conférences, par exemple. Les campagnes liées à des événements numériques (interactions ayant lieu sur votre site web) ne doivent pas être synchronisées avec [!DNL Marketo Measure]. La synchronisation de ces campagnes entraînerait la duplication des points de contact, car le JavaScript [!DNL Marketo Measure] effectue déjà le suivi des efforts en ligne.

Une autre astuce pour gérer les campagnes pour les activités en ligne consiste à mapper le type de campagne [!DNL Salesforce] sur NULL. Pour ce faire, créez d’abord un canal dans l’application [!DNL Marketo Measure] intitulé NULL, comme illustré dans l’image ci-dessous. Elle se trouve dans l’application [!DNL Marketo Measure] sous la section **Créer des canaux**. Cela s’avère utile en cas de synchronisation accidentelle d’une campagne qui ne doit pas être synchronisée. Il est facile de trouver la campagne et de corriger le statut de synchronisation en examinant tout ce qui est regroupé sous NULL.

![Une autre astuce pour gérer les campagnes pour les activités en ligne consiste à mapper les ](assets/offline-channels-14.png)

## Saisie de vos règles de canal hors ligne dans l’application {#entering-your-offline-channel-rules-to-the-app}

Une fois que vous avez modifié et mis à jour la feuille de calcul avec vos règles personnalisées, l’étape suivante consiste à recréer ce mappage de canal dans l’application [!DNL Marketo Measure]. En fait, vous ne chargerez pas de feuille de calcul pour les canaux hors ligne. Vous devez plutôt saisir les informations dans les zones de liste de sélection, comme illustré dans l’image ci-dessous. Pour ce faire, cliquez sur **[!UICONTROL Canaux hors ligne]** dans la section **[!UICONTROL Canaux]**.

![Une fois que vous avez modifié et mis à jour la feuille de calcul avec vos règles personnalisées, le](assets/offline-channels-20.png)

>[!TIP]
>
>Vous souhaitez déterminer _quand_ un type de campagne [!DNL Salesforce] est extrait dans [!DNL Marketo Measure] mappage de canal ? Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Campagnes]** > **[!UICONTROL Champs]** > **[!UICONTROL Type]**. Vous pouvez ensuite voir quelles valeurs se trouvent dans la liste de sélection et lesquelles sont inactives. Les canaux inactifs ne s’affichent pas en tant que type sélectionnable dans notre section « [!UICONTROL  Canaux hors ligne ] ». Notez que ce processus peut prendre de quelques minutes à 48 heures.

Cliquez sur **[!UICONTROL Enregistrer]** lorsque vous avez terminé. [!DNL Marketo Measure] chargerez les modifications et retraiterez les données.

>[!MORELIKETHIS]
>
>* [[!DNL Marketo Measure] Tutoriels : Mappage de canaux hors ligne](https://experienceleague.adobe.com/fr/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/mapping-offline-channels){target="_blank"}
>
>* [[!DNL Marketo Measure] Tutoriels : Synchroniser des campagnes hors ligne](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/syncing-offline-campaigns){target="_blank"}
>
>* [Intégration des programmes Marketo Engage](/help/marketo-engage-programs-integration.md){target="_blank"}
