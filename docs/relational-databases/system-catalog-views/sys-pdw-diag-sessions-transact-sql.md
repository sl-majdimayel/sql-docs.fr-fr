---
title: sys.pdw_diag_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bd48648719e04ca1eec15c4594b08cc1d40505b9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028630"
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations concernant les différentes sessions de diagnostic qui ont été créés sur le système.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**nom**|**nvarchar(255)**|Nom de la session de diagnostic.<br /><br /> Clé pour cette vue.||  
|**xml_data**|**nvarchar(4000)**|Charge utile XML décrivant la session.||  
|**is_active**|**bit**|Indicateur qui spécifie si l’indicateur est actif.||  
|**host_address**|**nvarchar(255)**|Adresse de l’ordinateur qui héberge la définition de session (nœud de contrôle).||  
|**principal_id**|**Int**|ID de l’utilisateur qui a créé la session au niveau de la base de données.||  
|**database_id**|**Int**|ID de la base de données qui est la portée de la session de diagnostic.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
