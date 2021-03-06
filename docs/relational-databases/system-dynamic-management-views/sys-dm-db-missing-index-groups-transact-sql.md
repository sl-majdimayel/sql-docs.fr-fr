---
title: Sys.dm_db_missing_index_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_groups
- sys.dm_db_missing_index_groups_TSQL
- dm_db_missing_index_groups
- dm_db_missing_index_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_groups dynamic management view
- missing indexes feature [SQL Server], sys.dm_db_missing_index_groups dynamic management view
ms.assetid: 9cc00acd-d83d-49f8-be72-5b2aebed246b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f205632359b7bd40f446ced41cccdf43e984709b
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52406436"
---
# <a name="sysdmdbmissingindexgroups-transact-sql"></a>sys.dm_db_missing_index_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Cette DMV retourne des informations sur les index qui ne figurent pas dans un groupe d’index spécifique, à l’exception des index spatiaux. 
  
 Dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d’exposer ces informations, chaque ligne qui contient les données qui n’appartient pas au locataire connecté est filtrée.  
   
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**index_group_handle**|**Int**|Identifie un groupe d'index manquants.|  
|**index_handle**|**Int**|Identifie un index manquant qui appartient au groupe spécifié par **index_group_handle**.<br /><br /> Un groupe d'index ne contient qu'un seul index.|  
  
## <a name="remarks"></a>Notes  
 Informations retournées par **sys.dm_db_missing_index_groups** est mis à jour lorsqu’une requête est optimisée par l’optimiseur de requête et n’est pas persistant. Les informations sur les index manquants sont simplement conservées jusqu'au redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les administrateurs de base de données doivent effectuer régulièrement des copies de sauvegarde des informations sur les index manquants s'ils souhaitent les conserver après le recyclage du serveur.  
  
 Aucune des deux colonnes de l'ensemble de résultats de sortie n'est une clé, mais ensemble, les colonnes constituent une clé d'index.  

  >[!NOTE]
  >Le jeu de résultats pour cette DMV sont limité à 600 lignes. Chaque ligne contient un index manquant. Si vous avez plus de 600 index manquants, vous devez traiter l’index manquants existants, donc vous pouvez ensuite afficher les plus récents.
  
## <a name="permissions"></a>Autorisations  
 Pour interroger cette vue de gestion dynamique, les utilisateurs doivent bénéficier de l'autorisation VIEW SERVER STATE ou de tout privilège qui implique l'autorisation VIEW SERVER STATE.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
