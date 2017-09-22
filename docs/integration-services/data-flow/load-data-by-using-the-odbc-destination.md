---
title: "Charger des données à l’aide de la Destination ODBC | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 339ec0a8-922e-48c0-97b3-fc5ee34f95e3
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 668cf193758a8dfaba90e598ccbdb7d0d84351fc
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="load-data-by-using-the-odbc-destination"></a>Charger des données à l'aide de la destination ODBC
  Cette procédure montre comment charger des données à l'aide de la destination ODBC. Pour pouvoir ajouter et configurer une destination ODBC, le package doit inclure au moins une tâche de flux de données et une source.  
  
### <a name="to-load-data-using-an-odbc-destination"></a>Pour charger des données à l'aide d'une destination ODBC  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] souhaité.  
  
2.  Cliquez sur l'onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser la destination ODBC sur l'aire de conception.  
  
3.  Faites glisser une sortie disponible d'un composant de flux de données dans l'entrée de la destination ODBC.  
  
4.  Double-cliquez sur la destination ODBC.  
  
5.  Dans la boîte de dialogue **Éditeur de destination ODBC** , dans la page **Gestionnaire de connexions** , sélectionnez un gestionnaire de connexions ODBC existant ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions.  
  
6.  Sélectionnez la méthode d'accès aux données.  
  
    -   **Nom de la table - Lot**: sélectionnez cette option pour configurer la destination ODBC de manière à utiliser le mode de traitement par lots. Lorsque vous sélectionnez cette option, vous pouvez définir **Taille du lot**.  
  
    -   **Nom de la table - Ligne par ligne**: sélectionnez cette option pour configurer la destination ODBC de manière à insérer les lignes de la table de destination une par une. Lorsque vous sélectionnez cette option, les données sont chargées dans la table une ligne à la fois.  
  
7.  Dans le champ **Nom de la table ou de la vue** , sélectionnez une table ou une vue disponible de la base de données dans la liste ou tapez une expression régulière pour identifier la table. Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1 000 tables, vous pouvez taper le début du nom d'une table ou utiliser le caractère générique (*) pour entrer une partie du nom afin d'afficher la table ou les tables que vous souhaitez utiliser.  
  
8.  Vous pouvez cliquer sur **Aperçu** pour afficher jusqu'à 200 lignes de données de la table sélectionnée dans la destination ODBC.  
  
9. Cliquez sur **Mappages** , puis mappez les colonnes de la liste **Colonnes d'entrée disponibles** aux colonnes de la liste **Colonnes de destination disponibles** en faisant glisser les colonnes d'une liste à l'autre.  
  
10. Pour configurer l'affichage des erreurs, cliquez sur **Sortie d'erreur**.  
  
11. Cliquez sur **OK**.  
  
12. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Destination ODBC &#40; Page Gestionnaire de connexions &#41;](../../integration-services/data-flow/odbc-destination-editor-connection-manager-page.md)   
 [Éditeur de Destination ODBC &#40; Page mappages &#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)   
 [Éditeur de Source ODBC &#40; Page sortie d’erreur &#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  