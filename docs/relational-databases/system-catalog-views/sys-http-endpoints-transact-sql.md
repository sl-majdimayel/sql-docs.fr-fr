---
title: Sys.http_endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.http_endpoints
- http_endpoints
- sys.http_endpoints_TSQL
- http_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.http_endpoints catalog view
ms.assetid: 16f59695-ecd9-457e-8874-055af63f8ea7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1bd36b58fc3a98e0c123e37a3b98c18077ac19ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735777"
---
# <a name="syshttpendpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque point de terminaison créé sur le serveur qui utilise le protocole HTTP.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**< colonnes héritées >**||Hérite des colonnes de [sys.endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**Site**|**nvarchar(128)**|Nom de l'ordinateur hôte du site, tel qu'il est spécifié dans l'option SITE =.|  
|**url_path**|**nvarchar(4000)**|Portion du chemin d'accès uniquement de ce point de terminaison HTTP, comme le spécifie l'option PATH=.|  
|**is_clear_port_enabled**|**bit**|1 = Activation du port en clair à l'aide de l'option PORT = CLEAR.|  
|**CLEAR_PORT**|**Int**|Numéro de port spécifié dans l'option CLEAR PORT =.<br /><br /> NULL = Non spécifié.|  
|**is_ssl_port_enabled**|**bit**|1 = Activation du port SSL à l'aide de l'option PORT = SSL.|  
|**SSL_PORT**|**Int**|Numéro de port spécifié dans l'option SSL PORT =.<br /><br /> NULL = Non spécifié.|  
|**is_anonymous_enabled**|**bit**|1 = Activation de l'accès anonyme à l'aide de l'option AUTHENTICATION = ANONYMOUS.|  
|**is_basic_auth_enabled**|**bit**|1 = Activation de l'authentification de base à l'aide de l'option AUTHENTICATION = BASIC.|  
|**is_digest_auth_enabled**|**bit**|1 = Activation de l'authentification de type Digest à l'aide de l'option AUTHENTICATION = DIGEST.|  
|**is_kerberos_auth_enabled**|**bit**|1 = Activation de l'authentification intégrée à l'aide de l'option AUTHENTICATION = KERBEROS.|  
|**is_ntlm_auth_enabled**|**bit**|1 = Activation de l'authentification intégrée à l'aide de l'option AUTHENTICATION = NTLM.|  
|**is_integrated_auth_enabled**|**bit**|1 = Activation de l'authentification intégrée à l'aide de l'option AUTHENTICATION = INTEGRATED.|  
|**authorization_realm**|**nvarchar(128)**|Indicateur retourné au client dans le cadre de la vérification de l'authentification DIGEST HTTP. Valeur de l'option AUTH REALM.<br /><br /> NULL si non spécifié ou si l'authentification DIGEST n'est pas activée.|  
|**DEFAULT_LOGON_DOMAIN**|**nvarchar(128)**|Domaine de connexion par défaut si vous activez l'authentification de base. Valeur de l'option DEFAULT LOGON DOMAIN.<br /><br /> NULL si non spécifié ou si l'authentification de base n'est pas activée.|  
|**is_compression_enabled**|**bit**|1 = L'option COMPRESSION = ENABLED est définie.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de points de terminaison &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
