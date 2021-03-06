---
title: Résolution des problèmes et Forum aux questions pour l’apprentissage - SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4a62dd0710a97a33f5a4703f194df2c6bcef2a54
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511886"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>Résoudre les problèmes de machine learning dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Utilisez cette page comme point de départ pour étudier des problèmes connus.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services (R et Python)

## <a name="known-issues"></a>Problèmes connus

Les articles suivants décrivent les problèmes connus avec les versions actuelles et précédentes :

+ [Problèmes connus pour R Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
+ [Notes de publication de SQL Server 2017](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>Comment recueillir des informations système

Si vous avez rencontré une erreur ou que vous devez comprendre un problème dans votre environnement, il est important que vous collectez des informations connexes systématiquement. L’article suivant fournit une liste d’informations qui facilite la résolution des problèmes d’auto-assistance ou d’une demande de support technique.

+ [Collecte de données pour la résolution des problèmes de l’apprentissage](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>Guides d’installation et configuration

Commencez ici si vous n’avez pas configuré de machine learning avec SQL Server, ou si vous souhaitez ajouter la fonctionnalité :

+ [Installation de SQL Server 2017 Machine Learning Services (en base de données)](install/sql-machine-learning-services-windows-install.md)
+ [Installer SQL Server 2017 Machine Learning Server (autonome)](install/sql-machine-learning-standalone-windows-install.md)
+ [Installer SQL Server 2016 R Services (en base de données)](install/sql-r-services-windows-install.md)
+ [Installer SQL Server 2016 R Server (autonome)](install/sql-r-standalone-windows-install.md)
+ [Programme d’installation de l’invite de commandes](install/sql-ml-component-commandline-install.md)
+ [Configuration en mode hors connexion (sans Internet)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>Configuration

Les articles suivants contiennent des informations sur les valeurs par défaut et comment personnaliser la configuration pour l’apprentissage automatique sur une instance :

+ [Exécution simultanée de mise à l’échelle de scripts externes dans SQL Server Machine Learning Services](administration/modify-user-account-pool.md)   
+ [Configurer et gérer les extensions d’analytique avancée](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [Comment créer un pool de ressources](r/how-to-create-a-resource-pool-for-r.md)
+ [Optimisation pour les charges de travail R](r/operationalizing-your-r-code.md)
