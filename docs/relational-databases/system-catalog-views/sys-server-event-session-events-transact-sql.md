---
title: Sys.server_event_session_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_session_events
- server_event_session_events_TSQL
- sys.server_event_session_events
- sys.server_event_session_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_events catalog view
- xe
ms.assetid: 75986e91-1fc7-4f14-98ac-4e90154a74db
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 766d614db7d07c8db5305c32a5e84d71dac53dca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681277"
---
# <a name="sysservereventsessionevents-transact-sql"></a>sys.server_event_session_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque événement d'une session d'événements.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**Int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|event_id|**Int**|ID de l'événement. Cet ID est unique au sein d'une session d'événements. N'accepte pas la valeur NULL.|  
|NAME|**sysname**|Nom de l’événement. N'accepte pas la valeur NULL.|  
|package|**sysname**|Nom du package d'événement qui contient l'événement. N'accepte pas la valeur NULL.|  
|module|**sysname**|Nom du module qui contient l'événement. N'accepte pas la valeur NULL.|  
|prédicat|**nvarchar(3000)**|L’expression de prédicat est appliquée à l’événement. Autorise la valeur NULL.|  
|predicate_xml|**nvarchar(3000)**|Expression de prédicat XML qui est appliquée à l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|From|Pour|Relation|  
|sys.server_event_session_events.event_session_id|Sys.server_event_sessions.event_session_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue des événements étendus &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
