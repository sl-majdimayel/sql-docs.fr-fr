---
title: "Utilisation de la base de connaissances par défaut DQS | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2012
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bbd80ca8bdeb9412646409eb08ba1955b31b75c4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-the-dqs-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut DQS
  Cette rubrique décrit la base de connaissances par défaut, **DQS Data**, qui est installée avec [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Il s'agit d'une base de connaissances par défaut prégénérée qui contient les domaines suivants :  
  
-   **Pays/Région**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/la région) et le nom court (nom commun utilisé dans les listes, sur les cartes, etc.), une abréviation à deux lettres, une abréviation à trois lettres et le code de trois chiffres pour chaque lieu.  La valeur principale est le nom long du pays.  
  
-   **Pays/Région (valeur principale de trois lettres)**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/région) et le nom court (nom commun utilisé dans les listes, sur des cartes, etc.), une abréviation à deux lettres, une abréviation à trois lettres et le code de trois chiffres pour chaque lieu.  Les valeurs principales sont l'abréviation de trois lettres pour Compté.  
  
-   **Pays/Région (valeur principale de deux lettres)**: contient le nom long conventionnel (nom officiel tel que désigné par le pays/la région) et le nom court (nom commun utilisé dans les listes, sur les cartes, etc.), une abréviation à deux lettres, une abréviation à trois lettres et le code de trois chiffres pour chaque lieu.  La valeur principale est l'abréviation de deux lettres pour Pays.  
  
-   **États-Unis - Comtés**: contient la liste des comtés américains.  
  
-   **États-Unis - Nom**: contient la liste des noms (de famille) survenant 100 fois ou plus dans le recensement 2000.  
  
-   **États-Unis - Emplacements**: contient la liste des emplacements des 50 états, du District de Columbia et de Porto Rico, extrait du recensement 2010.  
  
-   **États-Unis - État**: contient le nom long conventionnel (officiel) et l'abréviation à deux lettres de chaque État des États-unis. La valeur principale est le nom conventionnel de l'État.  
  
-   **États-Unis - État (en-tête à deux lettres)**: contient le nom long conventionnel (officiel) et l'abréviation à deux lettres de chaque État des États-unis. La valeur principale est l'abréviation de deux lettres pour le nom de l'État.  
  
## <a name="using-the-default-knowledge-base"></a>Utilisation de la base de connaissances par défaut  
 Vous pouvez utiliser la base de connaissances par défaut, Données DQS, comme suit :  
  
-   Démarrez et exécutez rapidement un projet de nettoyage de qualité des données à l'aide de la base de connaissances par défaut sans devoir créer d'abord une nouvelle base de connaissances dans DQS.  
  
-   Exécutez les activités de gestion du domaine, de découverte des connaissances ou de stratégie de correspondance sur la base de connaissances par défaut. Pour cela, cliquez sur **Ouvrir la base de connaissances** dans [Data Quality Client Home Screen](../data-quality-services/data-quality-client-home-screen.md), sélectionnez la base de connaissances **Données de DQS** dans l'écran **Ouvrir la base de connaissances** , puis sélectionnez l'activité requise dans la zone **Sélectionner une activité** . Cliquez sur **Suivant** pour continuer.  
  
-   Créez une nouvelle base de connaissances à l'aide de la base de connaissances par défaut. Pour créer une base de connaissances à partir d'une base de connaissances existante, consultez [Créer une base de connaissances](../data-quality-services/create-a-knowledge-base.md).  
  
-   Utilisez-la dans le [composant de nettoyage DQS de Integration Services](http://go.microsoft.com/fwlink/?LinkId=238830) et le [complément Master Data Services pour Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de connaissances et domaines DQS](../data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  