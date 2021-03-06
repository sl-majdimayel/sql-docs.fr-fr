---
title: Restaurer à partir de Power Pivot dans Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 75290c6b877c3bb10cd42fbb10f1c087310791d3
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072770"
---
# <a name="restore-from-power-pivot"></a>Restaurer à partir de PowerPivot
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Utilisez la fonctionnalité Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de SQL Server Management Studio pour créer une base de données model tabulaire sur une instance Analysis Services (exécutée en mode tabulaire) ou restaurer vers une base de données existante à partir d’un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] (.xlsx).  
  
> [!NOTE]  
>  Le modèle de projet Importer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de SQL Server Data Tools fournit des fonctionnalités similaires. Pour plus d’informations, consultez [importer à partir de Power Pivot](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md).  
  
 Lorsque vous utilisez la fonctionnalité Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], gardez à l’esprit les points suivants :  
  
-   Pour utiliser la fonctionnalité Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], vous devez être connecté en tant que membre du rôle des Administrateurs du serveur sur l’instance Analysis Services.  
  
-   Le compte de service de l'instance Analysis Services doit avoir des autorisations de lecture sur le classeur à partir duquel vous effectuez la restauration.  
  
-   Par défaut, lorsque vous restaurez une base de données à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], la propriété Informations d’emprunt d’identité de source de données de la base de données model tabulaire a la valeur Par défaut, qui spécifie le compte de service de l’instance Analysis Services. Nous vous recommandons de modifier les informations d'identification d'emprunt d'identité vers un compte d'utilisateur Windows dans les Propriétés de la base de données. Pour plus d’informations, consultez [l’emprunt d’identité](../../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
-   Les données du modèle de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sont copiées dans une base de données model tabulaire existante ou créée sur l’instance Analysis Services. Si votre classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contient des tables liées, elles seront recréées en tant que table sans source de données, similaire à une table créée à l’aide de l’option Coller dans une nouvelle table.  
  
### <a name="to-restore-from-power-pivot"></a>Pour restaurer à partir de PowerPivot  
  
1.  Dans SSMS, dans l’instance Active Directory vers laquelle vous souhaitez effectuer une restauration, cliquez avec le bouton droit sur **Bases de données**, puis cliquez sur **Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**.  
  
2.  Dans la boîte de dialogue **Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**, dans **Source de restauration**, dans **Fichier de sauvegarde**, cliquez sur **Parcourir**, puis sélectionnez un fichier .abf ou .xslx à partir duquel effectuer la restauration.  
  
3.  Dans **Destination de la restauration**, dans **Restaurer la base de données**, tapez un nom pour une nouvelle base de données ou une base de données existante. Si vous n'indiquez pas de nom, le nom du classeur est utilisé.  
  
4.  Dans **Emplacement de stockage**, cliquez sur **Parcourir**, puis sélectionnez un emplacement pour stocker la base de données.  
  
5.  Dans **Options**, conservez l'option **Inclure des informations sur la sécurité** activée. Lors d’une restauration à partir d’un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , ce paramètre ne s’applique pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de données Model tabulaire](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Importer depuis Power Pivot](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  
