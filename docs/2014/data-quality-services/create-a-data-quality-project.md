---
title: Créer un projet de qualité des données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: dff9b07ddf0bd5062c1e10a2d31fe2fe1fa5c50f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020170"
---
# <a name="create-a-data-quality-project"></a>Créer un projet de qualité des données
  Cette rubrique explique comment créer un projet de qualité des données à l'aide de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Un projet de qualité des données est utilisé pour exécuter l'activité de nettoyage ou de correspondance dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Vous devez disposer d'une base de connaissances appropriée à utiliser dans le projet de qualité des données pour l'activité de nettoyage ou de correspondance.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_kb_operator sur la base de données DQS_MAIN pour créer un projet de qualité des données.  
  
##  <a name="Create"></a> Créer un projet de qualité des données  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’application Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Nouveau projet de qualité des données**.  
  
3.  Dans l'écran **Nouveau projet de qualité des données** :  
  
    1.  Dans la zone **Nom** , entrez un nom pour le nouveau projet de qualité des données.  
  
    2.  (Facultatif) Dans la zone de **Description** , tapez une description du nouveau projet de qualité des données.  
  
    3.  Dans la liste **Utiliser la Base de connaissances** , cliquez pour sélectionner une base de connaissances à utiliser pour le projet de qualité des données. La zone **Détails de la base de connaissances : <nom_base_de_connaissances>** sur le côté droit affiche les noms de domaine disponibles dans la base de connaissances sélectionnée.  
  
    4.  Dans la zone **Sélectionner une activité** , cliquez sur l'activité que vous souhaitez exécuter à l'aide de ce projet de qualité des données :  
  
        -   **Nettoyage**: Sélectionnez cette activité pour nettoyer les données sources.  
  
        -   **Mise en correspondance**: Sélectionnez cette activité pour effectuer une correspondance. Cette activité est disponible uniquement si la base de connaissances sélectionnée pour le projet de qualité des données contient une stratégie correspondante.  
  
4.  Cliquez sur **Créer** pour créer un projet de qualité des données.  
  
##  <a name="FollowUp"></a> Suivi : Après avoir créé un projet de qualité des données  
 Après avoir créé un projet de qualité des données, un Assistant vous est proposé pour effectuer l'activité sélectionnée : nettoyage ou correspondance. Pour plus d’informations sur les activités de nettoyage et de correspondance, consultez [Nettoyage des données](../../2014/data-quality-services/data-cleansing.md) et [Correspondance de données](../../2014/data-quality-services/data-matching.md).  
  
  
