---
title: Création de cluster Azure HDInsight, tâche | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f41d86d0f757f9ccd0e698ac1bc81423a3118bb9
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58386527"
---
# <a name="azure-hdinsight-create-cluster-task"></a>Tâche de création d’un cluster Azure HDInsight
La **tâche de création de cluster Azure HDInsight** permet à un package SSIS de créer un cluster Azure HDInsight dans le groupe de ressources et l’abonnement Azure spécifiés.
  
> [!NOTE]  
> - La création d’un cluster HDInsight peut prendre 10 à 20 minutes.  
> - Il existe un coût associé à la création et à l’exécution d’un cluster Azure HDInsight. Pour plus d’informations, consultez [Tarification HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/).  
  
Pour ajouter une **tâche de création de cluster Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de création de cluster Azure HDInsight** .  
  
Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Field**|**Description**|  
|AzureResourceManagerConnection|Sélectionnez un gestionnaire de connexions Azure Resource Manager existant ou créez-en un qui sera utilisé pour créer le cluster HDInsight.|  
|AzureStorageConnection|Sélectionnez un gestionnaire de connexions Azure Storage existant ou créez-en un nouveau qui fait référence à un compte Azure Storage qui sera associé au cluster HDInsight.|
|SubscriptionId|Spécifiez l’ID de l’abonnement dans lequel le cluster HDInsight sera créé.|
|ResourceGroup|Spécifiez le groupe de ressources Azure dans lequel le cluster HDInsight sera créé.|
|Emplacement|Spécifiez l’emplacement du cluster HDInsight. Le cluster doit être créé au même emplacement que le compte de stockage Azure spécifié.|  
|ClusterName|Spécifiez un nom pour le cluster HDInsight à créer.|  
|ClusterSize|Spécifiez le nombre de nœuds à créer dans le cluster.|  
|BlobContainer|Spécifiez le nom du conteneur de stockage par défaut à associer au cluster HDInsight.|  
|UserName|Spécifiez le nom d’utilisateur à utiliser pour la connexion au cluster HDInsight.|  
|Mot de passe|Spécifiez le mot de passe à utiliser pour la connexion au cluster HDInsight.|
|SshUserName|Spécifiez le nom d’utilisateur utilisé pour accéder à distance au cluster HDInsight à l’aide de SSH.|
|SshPassword|Spécifiez le mot de passe utilisé pour accéder à distance au cluster HDInsight à l’aide de SSH.|
|FailIfExists|Spécifiez si la tâche doit échouer si le cluster existe déjà.|  
  
> [!NOTE]  
> L’emplacement du cluster HDInsight et celui du compte de stockage Azure doivent être identiques.
