---
description: Découvrez comment gérer les erreurs dans les exportations CRM
title: Gestion des erreurs pour les exports CRM
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 8%

---

# Gestion des erreurs pour les exports CRM

Le paramètre Pause lors des erreurs d’exportation se trouve sous **Mon compte** > **Paramètres** > **CRM** > **Général**. Il vous permet de contrôler si les tâches d’exportation CRM doivent être suspendues en cas d’erreur au niveau de l’enregistrement.

>[!NOTE]
>
>Cette fonction n’est visible que si la fonction « Exporter vers le CRM » est activée.

Lorsque cette fonctionnalité est activée, la tâche d’exportation cesse de progresser et reste dans l’enregistrement où l’erreur s’est produite, jusqu’à ce que le problème soit résolu. Ces erreurs sont généralement dues à des autorisations manquantes, à des règles de validation personnalisées incorrectement appliquées ou à des problèmes de workflows/déclencheurs. Le traitement continue de s’exécuter comme prévu et tente automatiquement d’exporter à nouveau l’enregistrement en échec jusqu’à ce qu’il réussisse.

Si vous choisissez de désactiver cette fonctionnalité, une fenêtre contextuelle d’avertissement s’affiche, vous informant que cela peut entraîner des incohérences dans les données. Il est de votre responsabilité de résoudre les problèmes qui peuvent découler de ces incohérences.

Que la fonction soit activée ou désactivée, toutes les erreurs au niveau des enregistrements rencontrées sont consignées dans la table `ExportErrors` et la tâche `CRMExport_ExportError` tentera automatiquement de réexporter ces enregistrements quotidiennement. Cela élimine la nécessité d’une demande d’assistance pour lancer une réexportation, car cela se produit automatiquement sans intervention de l’équipe de développement.

Pourquoi le comportement d’arrêt de tâche est-il nécessaire compte tenu de la fonctionnalité de `ExportErrors` ? En interrompant les traitements d’exportation CRM standard à un enregistrement spécifique, le dépannage devient beaucoup plus facile. Il vous permet d’exécuter des tâches localement et d’empêcher la création d’un nombre potentiellement élevé d’erreurs d’exportation, qui devraient être récupérées et traitées pendant la réexportation.

Cette fonctionnalité peut être activée ou désactivée en fonction de votre comportement préféré. Par exemple, si vous rencontrez un code d’erreur particulièrement difficile et que vous préférez accepter temporairement les données « incomplètes », vous pouvez désactiver la fonctionnalité. Une fois le problème résolu, vous pouvez réactiver la fonctionnalité pour vous assurer que les exportations futures sont complètes et précises.
