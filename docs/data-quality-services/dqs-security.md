---
title: "Sécurité dans DQS | Microsoft Docs"
ms.custom: 
ms.date: 10/01/2012
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ec0b75c2d32bb45c74082a0235ce51decaf09c02
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="dqs-security"></a>Sécurité dans DQS
  L'infrastructure de sécurité [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) est basée sur l'infrastructure de sécurité SQL Server. Un administrateur de base de données accorde à un utilisateur un jeu d'autorisations en associant l'utilisateur à un rôle DQS. Cette opération détermine les ressources DQS auxquelles l'utilisateur a accès ainsi que les activités fonctionnelles que l'utilisateur est autorisé à effectuer.  
  
## <a name="dqs-roles"></a>Rôles DQS  
 Il existe quatre rôles pour DQS. L'un d'eux est l'administrateur de base de données qui s'occupe principalement de l'installation du produit, de la maintenance de la base de données et de la gestion des utilisateurs. Ce rôle utilise principalement SQL Server Management Studio, plutôt que l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Son rôle serveur est sysadmin.  
  
 Les trois autres rôles sont les travailleurs de l'information, les gestionnaires de données qui utilisent le produit directement en travaillant dans l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Il s'agit des rôles suivants :  
  
-   L' **administrateur DQS** (rôle dqs_administrator) peut effectuer toutes les opérations dans l'étendue du produit. L'administrateur peut modifier et exécuter un projet, créer et modifier une base de connaissances, terminer une activité, arrêter un processus dans une activité et modifier les paramètres de configuration et de services de données de référence. L'administrateur DQS ne peut pas, toutefois, installer le serveur ni ajouter de nouveaux utilisateurs. L'administrateur de base de données doit effectuer ces opérations.  
  
-   L' **éditeur de base de connaissances DQS** (rôle dqs_kb_editor) peut effectuer toutes les activités DQS, sauf pour l'administration. L'éditeur de base de connaissances peut modifier et exécuter un projet, et créer et modifier une base de connaissances. Il peut voir les données d'analyse des activités, mais ne peut pas terminer ni arrêter une activité, ni remplir des fonctions d'administration.  
  
-   L' **opérateur de base de connaissances DQS** (rôle dqs_kb_operator) peut modifier et exécuter un projet. Il ne peut effectuer aucun type de gestion des connaissances ; il ne peut pas créer ni modifier une base de connaissances. Il peut voir les données d'analyse des activités, mais ne peut pas terminer une activité ni remplir des fonctions d'administration.  
  
## <a name="user-management"></a>Gestion des utilisateurs  
 L'administrateur de base de données (DBA) crée des utilisateurs DQS et les associe à des rôles DQS dans SQL Server Management Studio. Il gère leurs autorisations en ajoutant des connexions SQL en tant qu'utilisateurs de la base de données DQS_MAIN, puis en associant chaque utilisateur à un des rôles DQS. Chaque rôle reçoit des autorisations sur un ensemble de procédures stockées dans la base de données DQS_MAIN. Les trois rôles DQS ne sont pas disponibles pour les bases de données DQS_PROJECTS et DQS_STAGING_DATA.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment créer un utilisateur et accorder des rôles DQS à l'aide de SQL Server Management Studio.|[Gérer des utilisateurs DQS dans SSMS](http://msdn.microsoft.com/library/955af01d-00da-4c51-9311-f3848749df54)|  
  
  