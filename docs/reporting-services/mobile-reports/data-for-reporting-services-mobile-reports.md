---
title: "Les données de rapports mobiles Reporting Services | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
caps.latest.revision: 15
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 105f4ca9859a2c8f0d16cb5e961dc1e395a83b62
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="data-for-reporting-services-mobile-reports"></a>Data for Reporting Services mobile reports
Le modèle de données [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] est simple. Les données sont importées dans [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] comme une collection de datasets. Des relations formelles entre les datasets ne sont pas nécessaires. Les recherches entre deux datasets fonctionnent tant que les valeurs de clé correspondent. Les agrégations de date/heure sont traitées par le composant d’exécution de rapport mobile. Elles correspondent entre différents datasets, même si la granularité des données d’horodatage varie selon les datasets.   
  
Vous pouvez importer les données de deux types de sources :   
  
* **Fichiers Excel locaux**: sélectionnez un document Excel, puis la ou les feuilles de calcul à importer. Après l’importation, les données sont stockées dans la définition du rapport mobile. Pour actualiser les données provenant du fichier Excel d’origine, utilisez la commande **Actualiser les données** dans le coin supérieur droit de l’onglet [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] **Data** tab. En savoir plus sur [préparation des données Excel pour les rapports mobiles SSRS](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md).  
  
* **[! INCLURE[PRODUCT_NAME](/sql-docs/docs/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).   
  
  Pour plus d’informations, consultez [Obtenir des données à partir de datasets partagés dans l’Éditeur de rapports mobiles](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md).  
  
Après avoir importé des données dans [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)], la procédure de conception et de création de rapports mobiles est la même, quelle que soit la provenance des données.   
  
## <a name="connect-mobile-report-elements-to-data"></a>Connecter des éléments de rapport mobile aux données ##  
  
Chaque élément de l’ [!INCLUDE[PRODUCT_NAME](../../includes/short-product-name.md)] contient un ou plusieurs paramètres de données. Par exemple, l’élément Jauge radiale contient deux paramètres de données : Valeur principale et Valeur de comparaison. Chacun de ces paramètres pointe vers un champ (colonne) d’un dataset spécifique.   
  
Le composant d’exécution du rapport mobile fournit les valeurs agrégées de la jauge, selon les sélections de l’utilisateur. Notez que la valeur de comparaison de la même instance Jauge radiale peut être liée à un champ d’un autre dataset.   
  
### <a name="see-also"></a>Voir aussi  
-  [Prepare data for Reporting Services mobile reports](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Créer et publier des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [Get data from shared datasets](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [Conserver la mise en forme des dates pour Analysis Services dans les rapports mobiles](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  

