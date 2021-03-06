---
title: MSsubscription_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_properties
- MSsubscription_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_properties system table
ms.assetid: f96fc1ae-b798-4b05-82a7-564ae6ef23b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc3e113ab9ace64cac0d41cb34bdec1c44355e48
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779771"
---
# <a name="mssubscriptionproperties-transact-sql"></a>MSsubscription_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsubscription_properties** table contient des lignes pour les informations de paramètre requises pour exécuter les agents de réplication sur l’abonné. Cette table est stockée dans la base de données d'abonnés sur l'Abonné pour un abonnement extrait ou dans la base de données de distribution sur le serveur de distribution pour un abonnement envoyé.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**publication_type**|**Int**|Type de publication :<br /><br /> **0** = transactionnelle.<br /><br /> **2** = fusion.|  
|**publisher_login**|**sysname**|ID de connexion utilisé côté serveur de publication pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_password**|**nvarchar (524)**|Mot de passe (chiffré) utilisé côté serveur de publication pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**publisher_security_mode**|**Int**|Mode de sécurité implémenté sur le serveur de publication :<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] l’authentification SQL Server.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] l’authentification Windows.<br /><br /> **2** = les déclencheurs de synchronisation utilisent statique **sysservers** entrée pour effectuer un appel de procédure distante (RPC), et *publisher* doit être défini dans le **sysservers**table en tant que serveur distant ou serveur lié.|  
|**serveur de distribution**|**sysname**|Le nom du serveur de distribution.|  
|**distributor_login**|**sysname**|ID de connexion utilisé sur le serveur de distribution pour l’authentification SQL Server.|  
|**distributor_password**|**nvarchar (524)**|Mot de passe (chiffré) utilisé côté serveur de distribution pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_security_mode**|**Int**|Mode de sécurité implémenté sur le serveur de distribution :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.<br /><br /> **1** = l’authentification Windows.|  
|**ftp_address**|**sysname**|L’adresse réseau du service de fichier transfer protocol (FTP) pour le serveur de distribution.|  
|**ftp_port**|**Int**|Le numéro de port du service FTP du serveur de distribution.|  
|**ftp_login**|**sysname**|Nom d'utilisateur, utilisé pour la connexion au service FTP.|  
|**ftp_password**|**nvarchar (524)**|Mot de passe utilisateur, utilisé pour la connexion au service FTP.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Indique l'emplacement du dossier de remplacement pour l'instantané.|  
|**working_directory**|**nvarchar(255)**|Le nom du répertoire de travail utilisé pour stocker les fichiers de données et le schéma.|  
|**use_ftp**|**bit**|Spécifie l’utilisation de FTP au lieu du protocole usuel pour extraire les instantanés. Si **1**, FTP est utilisé.|  
|**argument dts_package_name**|**sysname**|Spécifie le nom du package DTS (Data Transformation Services).|  
|**dts_package_password**|**nvarchar (524)**|Spécifie le mot de passe du package.|  
|**dts_package_location**|**Int**|Emplacement de stockage du package DTS.|  
|**argument enabled_for_syncmgr**|**bit**|Spécifie s'il est possible de synchroniser l'abonnement à l'aide du Gestionnaire de synchronisation [!INCLUDE[msCoName](../../includes/msconame-md.md)].<br /><br /> **0** = abonnement n’est pas inscrit avec le Gestionnaire de synchronisation.<br /><br /> **1** = abonnement est enregistré avec le Gestionnaire de synchronisation et peuvent être synchronisé sans démarrer [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|  
|**offload_agent**|**bit**|Spécifie si l'Agent peut ou non être activé à distance. Si **0**, l’agent ne peut pas être activé à distance.|  
|**offload_server**|**sysname**|Indique le nom de réseau du serveur utilisé pour l'activation à distance.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Spécifie le chemin d'accès au dossier où les fichiers d'instantané sont enregistrés.|  
|**use_web_sync**|**bit**|Spécifie si l'abonnement peut ou non être synchronisé via HTTP. La valeur **1** signifie que cette fonctionnalité est activée.|  
|**internet_url**|**nvarchar(260)**|Adresse URL de l'emplacement de l'écouteur de réplication pour la synchronisation Web.|  
|**internet_login**|**sysname**|La connexion de l’Agent de fusion utilise pour se connecter au serveur Web qui héberge la synchronisation Web à l’aide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**internet_password**|**nvarchar (524)**|Le mot de passe pour la connexion de l’Agent de fusion utilise pour se connecter au serveur Web qui héberge la synchronisation Web à l’aide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**internet_security_mode**|**Int**|Le mode d’authentification utilisé lors de la connexion au serveur Web qui héberge la synchronisation Web, où la valeur **1** signifie que l’authentification Windows et la valeur **0** signifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentification.|  
|**internet_timeout**|**Int**|Durée (en secondes) avant l'expiration d'une demande de synchronisation Web.|  
|**Nom d’hôte**|**sysname**|Spécifie la valeur de **HOST_NAME** lorsque cette fonction est utilisée dans le **où** clause de filtre de jointure ou de la relation d’enregistrements logiques.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
