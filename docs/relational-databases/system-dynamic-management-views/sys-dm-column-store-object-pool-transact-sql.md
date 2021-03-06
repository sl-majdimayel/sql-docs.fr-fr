---
title: Sys.dm_column_store_object_pool (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a8a58ca7-0a7d-4786-bfd9-e8894bd345dd
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d9d88d2084533904dcbb47aad0d629b1aa8171e8
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52544241"
---
# <a name="sysdmcolumnstoreobjectpool-transact-sql"></a>Sys.dm_column_store_object_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Renvoie le nombre des différents types d’utilisation de pool de mémoire objet pour les objets d’index columnstore.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|ID de la base de données. Il est unique au sein d’une instance d’une base de données SQL Server ou un serveur de base de données SQL Azure. |  
|`object_id`|`int`|ID de l'objet. L’objet est un de l’object_types. | 
|`index_id`|`int`|ID de l'index columnstore.|  
|`partition_number`|`bigint`|Numéro de partition (basé sur la valeur 1) au sein de l'index ou du segment de mémoire. Chaque table ou la vue comporte au moins une partition.| 
|`column_id`|`int`|ID de la colonne columnstore. Il s’agit de la valeur NULL DELETE_BITMAP.| 
|`row_group_id`|`int`|ID du rowgroup.|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT - un segment de colonne. `object_id` est l’ID de segment. Un segment stocke toutes les valeurs pour une colonne au sein d’un groupe de lignes. Par exemple, si une table a 10 colonnes, il existe des segments de colonne 10 par groupe de lignes. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY - global dictionnaire qui contient des informations de recherche pour tous les segments de colonne dans la table.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY - un dictionnaire local associé à une colonne.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY - il s’agit d’une autre représentation du dictionnaire global. Ainsi, une recherche inversée de valeur à dictionary_id. Utilisé pour créer des segments compressés en tant que partie du moteur de Tuple ou de chargement en masse.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP - supprime de la bitmap qui effectue le suivi de segment. Il existe une seule bitmap de suppression par partition.|  
|`access_count`|`int`|Nombre de lire ou écrire les accès à cet objet.|  
|`memory_used_in_bytes`|`bigint`|Mémoire utilisée par cet objet dans le pool d’objets.|  
|`object_load_time`|`datetime`|Heure pour Lorsque object_id a été placée dans le pool d’objets.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
 
## <a name="see-also"></a>Voir aussi  
  
 [Fonctions et vues de gestion dynamique relatives aux index &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  
