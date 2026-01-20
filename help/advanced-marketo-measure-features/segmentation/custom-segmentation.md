---
unique-page-id: 18874604
description: Segmentation personnalisée - [!DNL Marketo Measure]
title: Segmentation personnalisée
exl-id: c20a2add-250e-45ff-97a6-1b1c03351b6a
feature: Segmentation
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Segmentation personnalisée {#custom-segmentation}

Les segments permettent de filtrer les données dans le tableau de bord du retour sur investissement [!DNL Marketo Measure] afin d’explorer plus en détail un jeu de données spécifique. Par exemple, un segment peut être défini par un territoire géographique ou un système de talus.

**Pourquoi une segmentation personnalisée ?**

La segmentation personnalisée vous permet de filtrer les points de contact par catégories (nom du filtre) et règles (valeurs du filtre). Les clients de niveau 1 obtiennent un segment, les clients de niveau 2 et plus obtiennent dix. Selon l’objet vers lequel pointe votre tableau de bord de retour sur investissement (lead ou contact), vous pouvez créer des segments en fonction des champs figurant dans l’objet de lead/contact. En outre, vous pourrez créer des segments en fonction de tous les champs trouvés sur l’objet d’opportunité.

**Quand la fonction de segmentation personnalisée est-elle utile ?**

La segmentation personnalisée peut être utilisée pour afficher les données d’un type d’enregistrement particulier. Une fois la logique de filtre mappée, vous devriez être en mesure d’afficher dans la vue Cascade de demandes du tableau de bord [!DNL Marketo Measure], les mêmes données que celles que vous verriez dans votre CRM.

**Comment puis-je le configurer ?**

>[!NOTE]
>
>La mise à jour des règles de segment va retraiter les données historiques.

Étape 1 : déterminez les informations que vous souhaitez afficher.

Avant d’utiliser cette fonctionnalité, déterminez les informations de point de contact en fonction desquelles vous souhaitez filtrer. N’oubliez pas d’utiliser les valeurs exactes dans votre CRM pour vos types d’enregistrements. La configuration filtre les points de contact de haut en bas du funnel marketing.

Étape 2 : connectez-vous et localisez la fonctionnalité [!UICONTROL Segments].

* Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous
* Sous l’onglet [!UICONTROL &#x200B; Mon compte &#x200B;], sélectionnez [!UICONTROL Paramètres]
* Sélectionnez [!UICONTROL Segments] dans les options de la barre latérale à gauche, sous la section [!UICONTROL Rapports]

Étape 3 - Comprendre les composants.

* Utilisez cette légende pour comprendre les différentes icônes figurant sur cette page

![](assets/1.png)

Étape 4 - Ajouter Des Règles De Filtrage.

* Tout d’abord, saisissez le nom de la catégorie. [!UICONTROL Type d’entreprise] est un exemple. Cliquez sur la coche lorsque vous avez terminé. Vous devez saisir un nom de catégorie avant de pouvoir ajouter des segments
* Cliquez sur le signe plus pour ajouter un segment
* Saisissez un nom de segment. Par exemple, vous pouvez avoir un segment pour Nouvelle entreprise, Partenaires, Renouvellement ou Vente incitative

![](assets/2.png)

* Cliquez sur l’icône plus pour afficher les champs de saisie de règle. Les options de la liste de sélection des champs extraient directement les champs de votre CRM

![](assets/3.png)

>[!NOTE]
>
>Les champs de formule ne peuvent pas être utilisés dans vos règles et n&#39;apparaîtront pas dans la liste de sélection. Étant donné que les formules calculent en arrière-plan et ne modifient pas un enregistrement, [!DNL Marketo Measure] ne pouvez pas détecter si un enregistrement correspond ou non à une règle.

* L&#39;option [!UICONTROL Valeur] n&#39;est pas une liste déroulante et sa valeur doit être saisie manuellement. Veillez à vérifier les valeurs dans votre organisation Salesforce
* Répétez ce processus pour les règles de segment Opportunités .
* La catégorie « Autre » est un segment par défaut qui capture tous les points de contact non définis. Vous pouvez modifier le nom du segment par défaut
* Cliquez sur l’icône corbeille pour supprimer une catégorie entière ou une règle individuelle d’une catégorie. Vous pouvez également cliquer sur l’icône en forme de crayon pour modifier la catégorie ou la règle
* Notez que vous disposez d’un bouton « [!UICONTROL Enregistrer] » et d’un bouton « Enregistrer et traiter ». Utilisez le bouton Enregistrer pour enregistrer votre travail et les modifications au fil du temps. Utilisez le bouton Enregistrer et traiter UNIQUEMENT une fois que vous avez vérifié que :

   * Votre mappage est correct
   * Vous avez ajouté tous les segments que vous souhaitez suivre dans une catégorie
   * Le bouton Enregistrer et traiter déclenche la [!DNL Marketo Measure] de synchroniser tous vos points de contact et d’appliquer les nouvelles informations que vous avez ajoutées. Ce processus prend 7 jours et les règles ne peuvent pas être modifiées au cours de cette période

**_Remarques supplémentaires:_**

Si les règles ne sont pas configurées pour les leads/contacts et les opportunités, vous ne verrez qu’une partie de vos données. Pour préciser, si vous ne configurez pas les règles d’opportunités, vous ne verrez que les données de lead/contact sans les opportunités qui y sont associées. Il en va de même si vous ne configurez pas de règles pour les leads/contacts : vous ne verrez que les opportunités sans les leads/contacts associés.

Lorsque vous avez terminé, cliquez d’abord sur [!UICONTROL Enregistrer], revérifiez tout, puis cliquez sur [!UICONTROL Enregistrer et traiter]. N’oubliez pas que vous ne pouvez pas modifier vos paramètres pendant sept jours après l’enregistrement et le traitement, car [!DNL Marketo Measure] est en train de reformater vos données pendant ce temps.

Si vous êtes un client Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut en tant que contact, n’utilisez pas les deux champs ci-dessous spécifiques au prospect ([en savoir plus](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).

* b2b.personStatus
* b2b.isConverted

**Comment enregistrer les rapports générés ?**

Vous ne pouvez pas enregistrer les rapports générés directement dans l’interface utilisateur d’. Toutefois, [!DNL Marketo Measure] enregistre les noms de segment dans l’URL afin de conserver un enregistrement de chaque rapport en marquant la page avec un signet.
