---
title: Architecture des éléments de rapports personnalisés| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 24457cb6a471b91666f4eb0792e1c8fa186eaf42
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56011830"
---
# <a name="custom-report-item-architecture"></a>Architecture des éléments de rapports personnalisés
  Un élément de rapport personnalisé est une extension du langage RDL (Report Definition Language) qui permet aux développeurs d’ajouter des fonctionnalités qui ne sont pas prises en charge en mode natif dans le langage RDL ou d’étendre les fonctionnalités de contrôles existants. Un élément de rapport personnalisé comprend deux composants principaux : le composant d'exécution et le composant de conception. Ces composants sont implémentés en tant qu'assemblys [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] et peuvent être écrits dans n'importe quel langage conforme CLS.  
  
## <a name="the-run-time-component"></a>Composant d’exécution  
 Le composant d'exécution pour un élément de rapport personnalisé est appelé par le processeur de rapports au moment de l'exécution. Le composant d'exécution accepte les données passées par le processeur de rapports au moment de l'exécution, traite ces données, puis retourne une image contenant l'élément de rapport personnalisé rendu.  
  
 ![Composant au moment de l’exécution des éléments de rapports personnalisés](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "Composant au moment de l’exécution des éléments de rapports personnalisés")  
  
## <a name="the-design-time-component"></a>Composant de conception  
 Le composant de conception autorise la définition et la manipulation de l'élément de rapport personnalisé dans l'interface du Concepteur de rapports dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Le composant de conception comprend plusieurs sous-contrôles qui contrôlent l'apparence et les propriétés de l'élément de rapport personnalisé dans l'environnement de conception.  
  
 ![Composant au moment de la conception des éléments de rapports personnalisés](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "Composant au moment de la conception des éléments de rapports personnalisés")  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un composant d’exécution d’éléments de rapport personnalisé](../custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Création d’un composant au moment de la conception d’éléments de rapport personnalisé](../custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Procédure : déployer un élément de rapport personnalisé](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
