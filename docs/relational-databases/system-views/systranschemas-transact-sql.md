---
title: systranschemas (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- systranschemas
- systranschemas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systranschemas system table
ms.assetid: 864c3966-cb61-4f2b-8939-ccda112de853
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3339cf1731c712cdfee7145390d5cc955c748a98
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52760701"
---
# <a name="systranschemas-transact-sql"></a>systranschemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **systranschemas** table est utilisée pour effectuer le suivi des modifications de schéma dans les articles publiés dans les publications transactionnelles et d’instantané. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**tabid**|**Int**|Identifie l'article de table sur lequel la modification de schéma s'est produite.|  
|**LSN de début**|**binaire**|Valeur LSN du début de la modification de schéma.|  
|**endlsn**|**binaire**|Valeur LSN de la fin de la modification de schéma.|  
|**typeid**|**Int**|Type de modification de schéma.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
