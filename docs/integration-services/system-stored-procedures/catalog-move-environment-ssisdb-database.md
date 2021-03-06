---
title: catalog.move_environment (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: b3fb5242-3c4c-4a87-b3e5-beb22fbab053
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aa3db05644d582574bad2fd04bdca55b8a9c174d
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58270970"
---
# <a name="catalogmoveenvironment-ssisdb-database"></a>catalog.move_environment (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Déplace un environnement d'un dossier vers un autre dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.move_environment [ @source_folder = ] source_folder  
    , [ @environment_name = ] environment_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Arguments  
 [ @source_folder = ] *source_folder*  
 Nom du dossier source, où l'environnement réside avant le déplacement. *source_folder* est de type **nvarchar(128)**.  
  
 [ @environment_name = ] *environment_name*  
 Nom de l'environnement qui sera supprimé. *environment_name* est de type **nvarchar(128)**.  
  
 [ @destination_folder = ] *destination_folder*  
 Nom du dossier de destination, où l'environnement réside après le déplacement. *destination_folder* est de type **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'environnement  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L'environnement n'existe pas dans le dossier source  
  
-   Le dossier de destination a déjà un environnement avec le même nom  
  
-   L’utilisateur n’a pas les autorisations appropriées  
  
## <a name="remarks"></a>Notes   
 Les références environnementales des projets ne suivent pas l'environnement pendant le déplacement. Les références environnementales doivent être mises à jour en conséquence. Cette procédure stockée réussira même si les références environnementales sont arrêtées en déplaçant un environnement. Les références environnementales doivent être mises à jour après que cette procédure stockée s'est achevée.  
  
> [!NOTE]  
>  Un projet peut avoir des références environnementales relatives ou absolues. Les références relatives font référence à l'environnement par nom et requièrent que l'environnement réside dans le même dossier que le projet. Les références absolues font référence à l'environnement par nom et dossier, et aux environnements qui résident dans un dossier différent de celui du projet.  
  
  
