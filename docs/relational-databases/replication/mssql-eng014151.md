---
title: MSSQL_ENG014151 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe24bc816174f7e3ee21d91bd7c2028427655e3c
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133110"
---
# <a name="mssqleng014151"></a>MSSQL_ENG014151
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14151|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Réplication-%s : échec de l'agent %s. %s|  
  
## <a name="explanation"></a>Explication  
 Cette erreur est émise pour tout échec d'un Agent de réplication. Le texte de la fin du message dépend du contexte de l'échec.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cette erreur peut se produire dans un certain nombre de situations ; utilisez l'une des approches ci-dessous selon le cas :  
  
-   Redémarrez l'Agent en échec pour voir s'il s'exécutera sans erreur. Pour plus d’informations, consultez [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) et [Concepts des exécutables de l’agent de réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Vérifiez dans l'historique de l'Agent et des travaux si d'autres erreurs se sont produites vers la même heure. Pour obtenir des informations sur l’affichage de l’état de l’agent et des détails de l’erreur dans le moniteur de réplication, consultez [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
-   Vérifiez que la connectivité de base fonctionne entre les ordinateurs auxquels accède l'Agent, puis connectez-vous à chaque ordinateur avec un utilitaire tel que [sqlcmd Utility](../../tools/sqlcmd-utility.md). Lors de la connexion, utilisez le même compte que celui qu'utilise l'Agent pour se connecter. Pour plus d'informations sur les autorisations requises pour chaque compte d'Agent, consultez [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Si l'erreur se produit lors de la création ou de l'application d'un instantané, vérifiez si les fichiers du répertoire d'instantané ne comportent pas d'erreurs. 
  
-   Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut fournir des pistes conduisant à l'erreur et/ou à d'autres messages d'erreur.  
  
## <a name="see-also"></a> Voir aussi  
 [Administration de l’Agent de réplication](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Agent de distribution de réplication](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agent de lecture du journal de réplication](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agent de fusion de réplication](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agent de lecture de la file d’attente de réplication](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Agent d'instantané de réplication](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
