---
title: Utiliser la messagerie de base de données plutôt que SQL Mail | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 6cba711740695f692f6c5bbca20c19353ef35c5f
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512644"
---
# <a name="use-database-mail-instead-of-sql-mail"></a>Utiliser la messagerie de base de données plutôt que SQL Mail
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie dans l'affichage catalogue sys.configurations si l'option de configuration au niveau serveur sqlmail XPs est définie sur ON.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 SQL Mail sera supprimé dans une version ultérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Pour envoyer du courrier, utilisez la messagerie de base de données.  
  
 SQL Mail s'exécute dans un processus interne à un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si SQL Mail arrête de fonctionner, il en sera de même pour le serveur. La messagerie de base de données s'exécute en dehors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un processus distinct, est évolutive et ne requiert pas l'installation des composants clients MAPI étendus sur le serveur de production.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
