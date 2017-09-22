---
title: "Activer l’intégration de Data Quality Services à Master Data Services | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
caps.latest.revision: 5
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 50488f539ba00055f4b515a41dca47594c5d3f0d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>Activer l'intégration de Data Quality Services avec Master Data Services
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], la fonctionnalité de mise en correspondance est assurée par Data Quality Services (DQS). Cette fonctionnalité doit être activée pour pouvoir être utilisée.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Une application Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et une base de données doivent exister.  
  
-   La fonctionnalité Data Quality Services et le Data Quality Client doivent être installés sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données MDS. Pour plus d’informations, consultez [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### <a name="to-enable-data-quality-services-integration"></a>Pour activer l'intégration de Data Quality Services  
  
1.  Ouvrez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Dans le volet gauche, cliquez sur **Configuration Web**.  
  
3.  Dans la page **Configuration web** , sélectionnez le site web et l’application web.  
  
4.  Dans la section **Activer l’intégration DQS** , cliquez sur **Activer l’intégration avec Data Quality Services**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Complément Master Data Services pour Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  