---
title: restorefile (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorefile
- restorefile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7414ca1c7d3ef3455aeb3b41c677ebc946a0e3d3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806803"
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par fichier restauré (y compris les fichiers restaurés indirectement, par nom de groupe de fichiers). Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**Int**|Numéro d'identification unique de l'opération de restauration correspondante. Références **RestoreHistory (restore_history_id)**.|  
|**file_number**|**NUMERIC(10,0)**|Numéro d'identification du fichier restauré. Ce numéro doit être unique dans chaque base de données. Sa valeur peut être NULL.<br /><br /> Si un instantané d'une base de données est rétabli, cette valeur est renseignée de la même façon que pour une restauration complète.|  
|**destination_phys_drive**|**nvarchar(260)**|Lecteur ou partition vers laquelle le fichier a été restauré. Sa valeur peut être NULL.<br /><br /> Si un instantané d'une base de données est rétabli, cette valeur est renseignée de la même façon que pour une restauration complète.|  
|**destination_phys_name**|**nvarchar(260)**|Nom du fichier, sans indication de lecteur ou de partition sur lequel le fichier a été restauré. Sa valeur peut être NULL.<br /><br /> Si un instantané d'une base de données est rétabli, cette valeur est renseignée de la même façon que pour une restauration complète.|  
  
## <a name="remarks"></a>Notes  
 Pour réduire le nombre de lignes dans cette table et dans d’autres tables d’historique de sauvegarde et, exécutez le [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [restorehistory &#40;Transact-SQL&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
