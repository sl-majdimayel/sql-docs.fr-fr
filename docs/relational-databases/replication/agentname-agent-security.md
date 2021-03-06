---
title: Sécurité de l’agent &lt;nom_agent&gt; | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e30f7ba7674327c23ff04a8cade7107832c512e7
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54131869"
---
# <a name="ltagentnamegt-agent-security"></a>Sécurité de l’agent &lt;nom_agent&gt;
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La page **\<Sécurité de l’agent <nom_agent>** permet de spécifier les comptes sous lesquels l’Agent de distribution (pour la réplication transactionnelle ou la réplication de capture instantanée) ou l’Agent de fusion (pour la réplication de fusion) s’exécutent et établissent les connexions aux ordinateurs d’une topologie de réplication. Pour plus d’informations sur les autorisations exigées par les agents et les bonnes pratiques en matière de sécurité de la réplication, consultez [Modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md) et [Bonnes pratiques en matière de sécurité de la réplication](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="options"></a>Options  
 Cliquez sur le bouton de propriétés (**...**) dans la ligne de chaque Abonné pour accéder à la boîte de dialogue **Sécurité de l'Agent de distribution** ou **Sécurité de l'Agent de fusion** . Cliquez sur **Aide** dans la boîte de dialogue qui s'affiche pour fournir plus d'informations sur les autorisations indispensables pour les comptes utilisés par les agents.  
  
 Après avoir entré les paramètres dans l'une des boîtes de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agent de l'Abonné**  
 Nom de chaque Abonné.  
  
 **Connexion au serveur de distribution**  
 S'affiche pour les réplications d'instantané et transactionnelle. Le contexte dans lequel la connexion au serveur de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par envoi de données, la connexion locale est celle du serveur de distribution. Ce champ affiche donc toujours : **Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité \<Ordinateur>\\<Connexion\>** pour les abonnements par émission de données.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les champs affichent : **Utiliser la connexion \<Connexion>**, **Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité\<Ordinateur>\\<Connexion\>**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion au serveur de publication et serveur de distribution**  
 S'affiche pour la réplication de fusion. Le contexte des connexions aux serveurs de publication et de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par envoi de données, la connexion locale est celle des serveurs de publication et de distribution. Ce champ affiche donc toujours : **Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité \<Ordinateur>\\<Connexion\>** pour les abonnements par émission de données.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les champs affichent : **Utiliser la connexion \<Connexion>**, **Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité\<Ordinateur>\\<Connexion\>**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion à l'Abonné**  
 Le contexte dans lequel la connexion à l'abonné s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par extraction, la connexion locale est celle de l'abonné. Ce champ affiche donc toujours : **Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité \<Ordinateur>\\<Connexion\>** pour les abonnements par émission de données.  
  
-   Pour les abonnements par émission de données, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les champs affichent : **Utiliser la connexion \<Connexion>**, **Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité\<Ordinateur>\\<Connexion\>**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## <a name="see-also"></a> Voir aussi  
 [Afficher et modifier les propriétés d’un abonnement par extraction](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Afficher et modifier les propriétés d’un abonnement par émission de données](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Identité et contrôle d’accès pour la réplication](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
