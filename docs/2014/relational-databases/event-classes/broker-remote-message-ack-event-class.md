---
title: Broker:Remote Message Ack, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Remote Message Ack event class
ms.assetid: 3d67efe1-74b4-4633-b029-c6e05b19f4dc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c919eb7c63a241c780d5e56b3e530921c6b51d6d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812261"
---
# <a name="brokerremote-message-ack-event-class"></a>Broker:Remote Message Ack, classe d'événements
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Remote Message Ack** lorsque [!INCLUDE[ssSB](../../includes/sssb-md.md)] envoie ou reçoit un accusé de réception de message.  
  
## <a name="brokerremote-message-ack-event-class-data-columns"></a>Colonnes de données de la classe d'événements Broker:Remote Message Ack  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs transmises par l'application au lieu de l'affichage du nom de programme.|10|Oui|  
|**BigintData1**|**bigint**|Numéro de séquence du message qui contient l'accusé de réception.|52|Non|  
|**BigintData2**|**bigint**|Numéro de séquence du message dont la réception est accusée.|53|Non|  
|**ClientProcessID**|**Int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par l'instruction USE *base de données* . Si aucune instruction USE *base de données* n’a été émise pour une instance donnée, ID de la base de données par défaut. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|**Int**|Type de classe d'événements capturée. Toujours **149** pour **Broker:Message Ack**.|27|Non|  
|**EventSequence**|**Int**|Numéro de séquence de cet événement.|51|Non|  
|**EventSubClass**|**nvarchar**|Type de sous-classe d'événements qui fournit des informations complémentaires sur chaque classe d'événements. Cette colonne peut contenir les valeurs ci-dessous :<br /><br /> **Message d’accusé de réception envoyé**<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] a envoyé un accusé de réception dans le cadre d’un message séquencé normal.<br /><br /> **Accusé de réception envoyé**<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] a envoyé un accusé de réception en dehors d’un message séquencé normal.<br /><br /> **Message d’accusé de réception reçu**<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] a reçu un accusé de réception dans le cadre d’un message séquencé normal.<br /><br /> **Accusé de réception reçu**<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] a reçu un accusé de réception en dehors d'un message séquencé.|21|Oui|  
|**GUID**|**uniqueidentifier**|ID de conversation du dialogue. Cet identifiant est transmis en tant que partie intégrante du message et est partagé par les deux intervenants de la conversation.|54|Non|  
|**HonorBrokerPriority**|**Int**|La valeur actuelle de l’option HONOR_BROKER_PRIORITY de la base de données : 0 = DÉSACTIVÉ, 1 = ON.|32|Oui|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IntegerData**|**Int**|Numéro de fragment du message qui contient l'accusé de réception.|25|Non|  
|**IntegerData2**|**Int**|Numéro de fragment du message dont la réception est accusée.|55|Non|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.<br /><br /> 0 = utilisateur<br /><br /> 1 = système|60|Non|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**Priorité**|**Int**|Niveau de priorité de la conversation.|5|Oui|  
|**RoleName**|**nvarchar**|Rôle de l'instance qui accuse réception du message. Il peut prendre la valeur **initiator** ou la valeur **target**.|38|Non|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SPID**|**Int**|ID de processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus qui est associé au client.|12|Oui|  
|**StartTime**|**datetime**|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**StarvationElevation**|**Int**|Le message a été envoyé avec une priorité plus élevée que la priorité qui a été configurée pour la conversation : 0 = Faux, 1 = true.|33|Oui|  
|**TransactionID**|**bigint**|ID affecté à la transaction par le système.|4|Non|  
  
  
