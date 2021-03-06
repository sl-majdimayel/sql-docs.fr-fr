---
title: Partitions dans les modèles tabulaires Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d26b1b1558ca546fb47660488b15dc777c5ad87
ms.sourcegitcommit: 2e8783e6bedd9597207180941be978f65c2c2a2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54405849"
---
# <a name="partitions"></a>Partitions
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les partitions créées à l’aide de la boîte de dialogue Partitions dans SSDT pendant la création du modèle s’appliquent à la base de données modèle espace de travail. Lorsque le modèle est déployé, les partitions définies pour la base de données model de l'espace de travail sont dupliquées dans la base de données model déployée. Vous pouvez créer et gérer des partitions pour une base de données model déployée à l’aide de la boîte de dialogue Partitions dans SSMS.  Les informations fournies dans cette rubrique décrivent les partitions créées pendant la création du modèle à l’aide de la boîte de dialogue Gestionnaire de Partition dans SSDT. Pour plus d’informations sur la création et la gestion des partitions pour un modèle déployé, consultez [créer et gérer des Partitions de modèles tabulaires](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_benefits"></a> Avantages  
 Les partitions, dans les modèles tabulaires, divisent une table en objets partition logiques. Chaque partition peut ensuite être traitée indépendamment d'autres partitions. Par exemple, une table peut comprendre certains ensembles de lignes qui contiennent des données qui changent rarement, alors que d'autres ensembles de lignes comportent des données qui changent souvent. Dans ces cas, il est inutile de traiter toutes les données lorsque vous pouvez vous contenter de traiter uniquement une partie des données. Les partitions permettent de diviser des parties de données devant être traitées fréquemment afin de les séparer des données qui peuvent être traitées moins souvent.  
  
 La création de modèles efficaces fait appel à des partitions permettant d'éliminer tout traitement inutile et la charge qui en résulte au niveau du processeur sur les serveurs Analysis Services, tout en veillant en même temps à ce que les données soient traitées et actualisées suffisamment souvent pour refléter les données les plus récentes des sources de données. La manière d'implémenter et d'utiliser des partitions lors de la création de modèles peut être très différente de la façon dont les partitions sont implémentées et utilisées pour les modèles déployés. Gardez à l'esprit que, pendant la phase de création de modèles, vous pouvez utiliser uniquement un sous-ensemble des données qui figureront au final dans votre modèle déployé.  
  
### <a name="processing-partitions"></a>Traitement de partitions  
 Pour les modèles déployés, le traitement se produit à l’aide de SSMS, ou en exécutant un script qui inclut la commande de processus et spécifie les paramètres et options de traitement. Lors de la création de modèles à l’aide de SSDT, vous pouvez exécuter des opérations de traitement en utilisant une commande de processus à partir du menu modèle ou la barre d’outils. Une opération de traitement peut être spécifiée pour une partition, une table ou les deux.  
  
 Lorsqu'une opération de traitement est exécutée, une connexion à la source de données est établie à l'aide de la connexion de données. Les nouvelles données sont importées dans les tables de modèle, les relations et les hiérarchies sont créées ou reconstruites pour chaque table, et les calculs des colonnes calculées et des mesures sont actualisés.  
  
 En divisant une table en partitions logiques, vous pouvez déterminer de manière sélective les éléments, la date et le mode de traitement des données dans chaque partition. Lorsque vous déployez un modèle, le traitement des partitions peut être effectué manuellement à l’aide de la boîte de dialogue Partitions dans SSMS, ou en utilisant un script qui exécute une commande de processus.  
  
### <a name="partitions-in-the-model-workspace-database"></a>Partitions dans la base de données model de l'espace de travail  
 Vous pouvez créer de nouvelles partitions, modifier, fusionner ou supprimer des partitions à l’aide du Gestionnaire de partitions dans SSDT. Selon le niveau de compatibilité du modèle que vous créez, Partition Manager propose deux modes de sélection des tables, lignes et colonnes d’une partition : Pour les modèles tabulaires 1400, les partitions sont définies à l’aide d’une requête M, ou vous pouvez utiliser le mode Création pour ouvrir l’éditeur de requête. Pour tabulaire 1100, 1103, 1200 modèles, utilisez le mode Aperçu de la Table et le mode de requête SQL. 
  
### <a name="partitions-in-a-deployed-model-database"></a>Partitions dans une base de données model déployée  
 Lorsque vous déployez un modèle, les partitions de la base de données model déployée apparaissent comme des objets de base de données dans SSMS. Vous pouvez créer, modifier, fusionner et supprimer des partitions pour un modèle déployé à l’aide de la boîte de dialogue Partitions dans SSMS. La gestion des partitions pour un modèle déployé dans SSMS sont en dehors de l’étendue de cette rubrique. Pour en savoir plus sur la gestion des partitions dans SSMS, consultez [créer et gérer des Partitions de modèles tabulaires](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Créer et gérer des partitions dans la base de données d’espace de travail](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)|Décrit comment créer et gérer des partitions dans la base de données modèle espace de travail à l’aide du Gestionnaire de Partition dans SSDT.|  
|[Traiter des partitions dans la base de données d’espace de travail](../../analysis-services/tabular-models/process-partitions-in-the-workspace-database-ssas-tabular.md)|Explique comment traiter (actualiser) des partitions dans la base de données model de l'espace de travail.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Traiter des données](../../analysis-services/tabular-models/process-data-ssas-tabular.md)  
  
  
