---
title: Méthode getPropertyInfo (SQLServerDriver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.getPropertyInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b5eaad8a-31ef-44ac-af11-d5caa13ac3e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 889f530496dd5fa975822702282cc78b99197318
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624847"
---
# <a name="getpropertyinfo-method-sqlserverdriver"></a>Méthode getPropertyInfo (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Utilisée pour découvrir les propriétés requises pour la connexion à une base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.DriverPropertyInfo[] getPropertyInfo(java.lang.String Url,  
                                                     java.util.Properties Info)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Url*  
  
 Valeur **String** contenant l’URL utilisée pour la connexion à la base de données.  
  
 *Info*  
  
 Liste de paires de valeurs de propriété, Null à la première utilisation.  
  
## <a name="return-value"></a>Valeur retournée  
 Un tableau d’objets de DriverPropertyInfo.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getPropertyInfo est spécifiée par la méthode getPropertyInfo dans l’interface java.sql.Driver.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDriver, méthodes](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver, membres](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
