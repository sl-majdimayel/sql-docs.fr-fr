---
title: "Traducteur spécification sous-clés | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62bfe54f5bd5117fee5d9ba063f1882be47ccbc4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="translator-specification-subkeys"></a>Traducteur spécification sous-clés
Chaque convertisseur répertorié dans la sous-clé ODBC traducteurs a une sous-clé qui lui sont propres. Cette sous-clé a le même nom que la valeur correspondante sous la sous-clé traducteurs de ODBC. Les valeurs sous cette sous-clé répertorient les chemins d’accès complets de la traduction et traducteur DLL ainsi que le nombre d’utilisations. Les formats des valeurs sont comme indiqué dans le tableau suivant.  
  
|Nom|Type de données|data|  
|----------|---------------|----------|  
|Convertisseur|REG_SZ|*chemin de DLL de traduction*|  
|Programme d'installation|REG_SZ|*le programme d’installation-DLL-path.*|  
|UsageCount|REG_DWORD|*nombre*|  
  
 Pour plus d’informations sur les compteurs d’utilisation, consultez [en prenant en compte l’utilisation](../../../odbc/reference/install/usage-counting.md) plus haut dans cette section.  
  
 Applications ne doivent pas définir le nombre d’utilisations. ODBC conserve ce nombre.  
  
 Par exemple, supposons que la Page de Code Microsoft Translator a une DLL nommée Mscpxl32.dll, situés dans la même DLL, les fonctions de traduction d’installation de la traduction et que le traducteur a été installé à trois reprises. Les valeurs sous la sous-clé de la Page de Code Microsoft Translator peuvent être comme suit :  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```