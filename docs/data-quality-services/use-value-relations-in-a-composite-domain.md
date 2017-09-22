---
title: Utiliser les relations de valeur dans un domaine composite | Microsoft Docs
ms.custom: 
ms.date: 11/22/2011
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c42159a2477e4eeba0afbaa536427cace2a5aafc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="use-value-relations-in-a-composite-domain"></a>Utiliser les relations de valeur dans un domaine composite
  Cette rubrique décrit comment afficher les combinaisons de valeurs trouvées pour le domaine composite pendant le processus de découverte des connaissances dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Cette page affiche le nombre d'occurrences des combinaisons de valeur. La gestion de valeur n'est pas prise en charge pour les domaines composites, vous ne pouvez donc pas exécuter d'opérations sur ces valeurs.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Prérequis  
 Pour afficher les relations de valeur, vous devez avoir créé et ouvert un domaine composite.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour afficher les relations de valeur dans un domaine composite.  
  
##  <a name="Use"></a> Afficher les relations de valeur  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , ouvrez ou créez une base de connaissances. Sélectionnez **Gestion de l'arborescence du domaine** comme activité, puis cliquez sur **Ouvrir** ou **Créer**. Pour plus d'informations, consultez [Créer une base de connaissances](../data-quality-services/create-a-knowledge-base.md) ou [Ouvrir une base de connaissances](../data-quality-services/open-a-knowledge-base.md).  
  
3.  Dans **Liste des domaines** de la page **Gestion de l'arborescence du domaine** , sélectionnez le domaine composite pour lequel vous souhaitez créer une règle de domaine, ou créez un nouveau domaine composite. Si vous devez créer un domaine, consultez [Créer un domaine composite](../data-quality-services/create-a-composite-domain.md).  
  
4.  Cliquez sur l'onglet **Relations de valeurs** .  
  
5.  Affichez les fréquences affichées pour chaque combinaison de valeurs.  
  
    > [!NOTE]  
    >  La table **Valeur** affiche chaque combinaison de valeurs qui existe dans le domaine composite. Chaque valeur est affichée dans le domaine simple auquel elle s'applique. Le tri par défaut de la table de relations de valeur se fait sur la fréquence, mais vous pouvez cliquer sur une autre colonne pour trier sur cette colonne. Seules les valeurs ayant une fréquence supérieure ou égale à 20 sont affichées.  
  
6.  Vous ne pouvez pas modifier l'une des valeurs de la table. Si vous avez exécuté d'autres opérations, cliquez sur **Terminer** pour terminer l'activité de gestion de domaine. Sinon, cliquez sur **Annuler**.  
  
##  <a name="FollowUp"></a> Suivi : Après affichage des relations de valeur  
 Après avoir affiché les relations de valeur, vous pouvez effectuer d'autres tâches de gestion des domaines sur le domaine, effectuer une découverte des connaissances pour ajouter des connaissances au domaine ou ajouter une stratégie de correspondance au domaine. Pour plus d’informations, consultez [Effectuer une découverte des connaissances](../data-quality-services/perform-knowledge-discovery.md), [Gestion d’un domaine](../data-quality-services/managing-a-domain.md) ou [Créer une stratégie de correspondance](../data-quality-services/create-a-matching-policy.md).  
  
  