---
title: DROP WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD CLASSIFIER
- WORKLOAD_CLASSIFIER_TSQL
- DROP_WORKLOAD_CLASSIFIER_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 915d689b90bf5103d276ee711e34102e05f49330
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513086"
---
# <a name="drop-workload-classifier-transact-sql-preview"></a>DROP WORKLOAD CLASSIFIER (Transact-SQL) (Préversion)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Supprime un classifieur de gestion des charges de travail défini par l’utilisateur existant.  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  

```
DROP WORKLOAD CLASSIFIER classifier_name;
```

## <a name="arguments"></a>Arguments

*classifier_name*  
Spécifie le nom qui identifie le classifieur de charge de travail.  classifier_name est de type sysname.  Il peut comporter jusqu’à 128 caractères et doit être unique dans l’instance.
  
## <a name="remarks"></a>Notes 

L’instruction DROP WORKLOAD CLASSIFIER n’est pas autorisée sur les classifieurs de charge de travail système.

Si des requêtes sont en cours d’exécution ou se trouvent dans la file d’attente des requêtes dans l’état suspendu, elles conserveront leur classification et le classifieur peut être supprimé immédiatement.  La suppression et la recréation du classifieur avec une importance différente n’affectent pas une requête déjà classifiée.

## <a name="permissions"></a>Autorisations

Exige l’autorisation CONTROL DATABASE.  
  
## <a name="examples"></a>Exemples

L’exemple suivant supprime le classifieur de charge de travail nommé `wgcELTROLE`.  

```sql
DROP WORKLOAD CLASSIFIER wgcELTRole;
```

> [!NOTE]
> Une requête envoyée sans classifieur correspondant est classifiée dans le groupe de charge de travail par défaut.  Le groupe de charge de travail par défaut est la classe de ressources smallrc.
  
## <a name="see-also"></a> Voir aussi

[CREATE WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-classifier-transact-sql.md)</br>
[Classification de charge de travail SQL Data Warehouse](/azure/sql-data-warehouse/classification)
