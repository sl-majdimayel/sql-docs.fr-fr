---
title: "DTAInput, élément (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 22a7b07a5dee4e826d2b438d384d44796ca23480
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="dtainput-element-dta"></a>DTAInput, élément (Assistant Paramétrage de base de données)
  Contient la définition de l'entrée XML pour l'Assistant Paramétrage du moteur de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristiques|Description|  
|---------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Obligatoire une fois par élément **DTAXML** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAXML, élément &#40; DTA &#41;](../../tools/dta/dtaxml-element-dta.md)|  
|**Éléments enfants**|[Élément de serveur &#40; DTA &#41;](../../tools/dta/server-element-dta.md)<br /><br /> [Workload, élément &#40; DTA &#41;](../../tools/dta/workload-element-dta.md)<br /><br /> [Tuningoptions, élément &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Élément de configuration &#40; DTA &#41;](../../tools/dta/configuration-element-dta.md)|  
  
## <a name="remarks"></a>Notes  
 Cet élément est la racine de la hiérarchie de schéma d'entrée de l'Assistant Paramétrage du moteur de base de données. Les entrées de l'Assistant Paramétrage du moteur de base de données peuvent être des arguments qui spécifient les bases de données à paramétrer, des charges de travail, des options de paramétrage ou une configuration spécifiée par l'utilisateur.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de l’élément **DTAInput**, consultez [Exemple de fichier d’entrée XML simple &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  