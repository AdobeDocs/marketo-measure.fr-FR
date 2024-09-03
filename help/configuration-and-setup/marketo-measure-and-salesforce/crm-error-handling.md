---
description: Découvrez comment gérer les erreurs dans les exportations CRM
title: Gestion des erreurs pour les exports CRM
feature: Salesforce
source-git-commit: ce5170330fb1d9f944762f401d29be4da5c0bd43
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 8%

---

# Gestion des erreurs pour les exports CRM

La fonction Mettre en pause lors de l’exportation des erreurs vous permet de contrôler si les tâches d’exportation CRM doivent être suspendues en cas d’erreur de niveau enregistrement.

Le paramètre se trouve sous **Mon compte** > **Paramètres** > **CRM** > **Général**.

![Suspendre les erreurs d’exportation](assets/stop-progress.png)

>[!NOTE]
>
>Cette fonctionnalité n’est visible que si la fonction &quot;Exporter vers le CRM&quot; est activée.

Lorsque cette fonction est activée, la tâche d’exportation cesse de progresser et reste dans l’enregistrement où l’erreur s’est produite, jusqu’à ce que le problème soit résolu. Ces erreurs sont généralement dues à des autorisations manquantes, à des règles de validation personnalisées incorrectement appliquées ou à des problèmes de workflows/déclencheurs. La tâche continue de s’exécuter comme prévu et tente automatiquement d’exporter l’enregistrement en échec jusqu’à ce qu’il soit réussi.

Si vous choisissez de désactiver cette fonction, une fenêtre contextuelle d’avertissement s’affiche, vous informant que cela peut entraîner des incohérences entre les données. Il vous appartiendra de résoudre tous les problèmes qui peuvent provenir de ces incohérences.

![Avertissement d’incohérence de données](assets/data-inconsistency.png)

Dans les deux cas, que la fonctionnalité soit activée ou désactivée, toutes les erreurs de niveau enregistrement rencontrées sont consignées dans la table `ExportErrors` et la tâche `CRMExport_ExportError` tentera automatiquement de réexporter ces enregistrements tous les jours. Cela évite d’avoir besoin d’une demande d’assistance pour lancer une réexportation, car cela se produit automatiquement sans intervention du développeur.

Pourquoi le comportement d’arrêt de la tâche est-il nécessaire en fonction de la fonctionnalité `ExportErrors` ? En arrêtant les tâches d’exportation CRM standard à un enregistrement spécifique, le dépannage devient beaucoup plus facile. Il vous permet d’exécuter des tâches localement et d’empêcher la création d’un nombre potentiellement important d’erreurs ExportErrors qui doivent être récupérées et traitées lors de la réexportation.

Cette fonctionnalité peut être activée ou désactivée en fonction de votre comportement préféré. Par exemple, si vous rencontrez un code d’erreur particulièrement problématique et que vous préférez accepter temporairement des données &quot;incomplètes&quot;, vous pouvez désactiver la fonction. Une fois le problème résolu, vous pouvez réactiver la fonction pour vous assurer que les prochaines exportations sont complètes et précises.
