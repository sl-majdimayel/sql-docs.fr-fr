---
title: Sys.messages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- messages_TSQL
- sys.messages_TSQL
- sys.messages
- messages
dev_langs:
- TSQL
helpviewer_keywords:
- error messages [SQL Server]
- sys.messages catalog view
- error numbers [SQL Server]
ms.assetid: 8c16ecdf-68f4-4a2a-b594-086e3344e58a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 215ff84696cfc3d7590777ab1a2ad0f17c48d2a6
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664075"
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>Affichages catalogue de messages (erreurs) - sys.messages
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque **message_id** ou **language_id** des messages d’erreur dans le système, pour les messages à la fois définie par le système et définies par l’utilisateur. Pour plus d’informations, consultez [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
   
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**message_id**|**Int**|ID du message. Unique sur le serveur. Les ID de message inférieurs à 50 000 sont des messages système.|  
|**ID_langue**|**smallint**|ID de langue pour laquelle le texte dans **texte** est utilisé, tel que défini dans **syslanguages**. Il est unique pour une certaine **message_id**.|  
|**severity**|**tinyint**|Niveau de gravité du message, entre 1 et 25. Il s’agit du même pour toutes les langues de message dans un **message_id**.|  
|**is_event_logged**|**bit**|1 = le message est consigné dans le journal des événements lorsqu'une erreur est déclenchée. Il s’agit du même pour toutes les langues de message dans un **message_id**.|  
|**texte**|**nvarchar(2048)**|Texte du message utilisée lorsque le correspondant **language_id** est actif.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Messages &#40;pour les erreurs&#41; affichages catalogue &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [Message d’exception programmation de boîte](https://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [Messages d’erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [Erreurs et événements du moteur de base de données](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
