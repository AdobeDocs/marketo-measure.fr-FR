---
unique-page-id: 18874604
description: Segmentation personnalisée - [!DNL Marketo Measure]
title: Segmentation personnalisée
exl-id: c20a2add-250e-45ff-97a6-1b1c03351b6a
feature: Segmentation
source-git-commit: e1ad563aac12ceb6bea6c28621ebd1cb7ec0a923
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Segmentation personnalisée {#custom-segmentation}

Les segments permettent de filtrer les données dans le tableau de bord du retour sur investissement [!DNL Marketo Measure] afin d’approfondir l’analyse d’un jeu de données spécifique. Par exemple, un segment peut être défini par un territoire géographique ou un système de classement.

**Pourquoi la segmentation personnalisée ?**

La segmentation personnalisée vous permet de filtrer les points de contact par catégories (nom du filtre) et règles (valeurs de filtre). Les clients de niveau 1 obtiennent un segment, les niveaux 2 et plus dix. Selon l’objet vers lequel pointe votre tiret de retour sur investissement (prospect ou contact), vous pouvez créer des segments en fonction des champs figurant dans l’objet de piste/contact. Vous pourrez également créer des segments en fonction de n’importe quel champ de l’objet d’opportunité.

**Quand la fonction de segmentation personnalisée est-elle utile ?**

La segmentation personnalisée peut être utilisée pour afficher les données d’un type d’enregistrement particulier. Une fois que vous avez mappé la logique de filtre, vous devriez être en mesure de voir dans la vue de la cascade de la demande du tableau de bord [!DNL Marketo Measure], les mêmes données que celles que vous verriez dans votre gestion de la relation client.

**Comment puis-je le configurer ?**

>[!NOTE]
>
>La mise à jour des règles de segmentation va retraiter les données historiques.

Étape 1 - Déterminer les informations que vous souhaitez voir.

Avant d’utiliser cette fonction, déterminez les informations de point de contact que vous souhaitez filtrer. N’oubliez pas d’utiliser les valeurs exactes dans votre CRM pour vos types d’enregistrements. La configuration va filtrer les points de contact du haut vers le bas de l’entonnoir marketing.

Étape 2 - Connectez-vous et recherchez la fonction [!UICONTROL Segments] .

* Accédez à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} et connectez-vous
* Sous l’onglet [!UICONTROL Mon compte], sélectionnez [!UICONTROL Paramètres]
* Sélectionnez [!UICONTROL Segments] parmi les options de la barre latérale gauche, sous la section [!UICONTROL Création de rapports] .

Étape 3 - Comprendre les composants.

* Utilisez cette légende pour comprendre les différentes icônes de cette page.

![](assets/1.png)

Étape 4 - Ajout de règles de filtrage.

* Saisissez tout d’abord le nom de la catégorie. [!UICONTROL Business Type] est un exemple. Cliquez sur la coche lorsque vous avez terminé. Vous devez saisir un nom de catégorie avant d’ajouter des segments.
* Cliquez sur le signe plus pour ajouter un segment.
* Saisissez un Nom de segment. Par exemple, vous pouvez avoir un segment pour Nouvelle entreprise, Partenaires, Renouvellement ou Mise à niveau.

![](assets/2.png)

* Cliquez sur l’icône plus pour afficher les champs de saisie de règle. Les options de la liste de sélection de champs extrait directement les champs de votre CRM.

![](assets/3.png)

>[!NOTE]
>
>Les champs de formule ne peuvent pas être utilisés dans vos règles et n’apparaîtront pas dans la liste de sélection. Comme les formules sont calculées en arrière-plan et ne modifient pas d’enregistrement, [!DNL Marketo Measure] ne peut pas détecter si un enregistrement correspond ou non à une règle.

* L&#39;option [!UICONTROL Valeur] n&#39;est pas une liste déroulante et sa valeur doit être saisie manuellement. Veillez à vérifier les valeurs de votre organisation Salesforce.
* Répétez ce processus pour les règles de segment Opportunités .
* La catégorie &quot;Autre&quot; est un segment par défaut qui capture tous les points de contact non définis. Vous pouvez modifier le nom du segment par défaut.
* Cliquez sur l’icône de corbeille pour supprimer une catégorie entière ou une règle individuelle dans une catégorie. Vous pouvez également cliquer sur l’icône en forme de crayon pour modifier la catégorie ou la règle.
* Notez que vous disposez d’un bouton &quot;[!UICONTROL Save]&quot; et d’un bouton &quot;Save and Process&quot;. Utilisez le bouton Enregistrer pour enregistrer votre travail et vos modifications au fil du temps. Utilisez le bouton Save and Process UNIQUEMENT une fois que vous avez vérifié que :

   * Votre mappage est précis
   * Vous avez ajouté tous les segments dont vous souhaitez effectuer le suivi dans une catégorie.
   * Le bouton Enregistrer et processus déclenche [!DNL Marketo Measure] la synchronisation de tous vos points de contact et l’application des nouvelles informations que vous avez ajoutées. Ce processus prend 7 jours et les règles ne peuvent pas être modifiées pendant cette période.

**_Remarques supplémentaires :_**

Si les règles ne sont pas configurées pour les pistes/contacts et les opportunités, seules une partie de vos données s’affiche. Pour plus d’informations, si vous ne configurez pas les règles d’opportunités, vous verrez uniquement les données de piste/contact sans les opportunités qui y sont associées. Il en va de même si vous ne définissez pas de règles pour les Leads/Contacts, vous ne verrez que les opportunités sans les Leads/Contacts associés.

Une fois que vous avez terminé, cliquez d’abord sur [!UICONTROL Enregistrer], double-vérifiez tout, puis cliquez sur [!UICONTROL Enregistrer et processus]. N’oubliez pas que vous ne pouvez pas modifier vos paramètres pendant les sept jours qui suivent l’enregistrement et le traitement, car [!DNL Marketo Measure] reformate vos données pendant cette période.

Si vous êtes un client Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut comme Contact, n’utilisez pas les deux champs ci-dessous spécifiques au prospect ([en savoir plus](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).

* b2b.personStatus
* b2b.isConverted

**Comment enregistrer les rapports générés ?**

Vous ne pouvez pas enregistrer les rapports générés directement dans l’interface utilisateur. Cependant, [!DNL Marketo Measure] enregistre les noms de segment dans l’URL afin que vous puissiez conserver un enregistrement de chaque rapport en marquant la page.
