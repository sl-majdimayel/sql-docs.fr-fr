---
title: getMetaData, méthode (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 86223cb5-3bf4-489a-8c82-669a91764f2b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: abb599adfe93935bd329d174b685ce71c2f64864
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47615127"
---
# <a name="getmetadata-method-sqlserverconnection"></a>getMetaData, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un objet [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) contenant des métadonnées sur la base de données pour laquelle cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) représente une connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.DatabaseMetaData getMetaData()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 L’objet DatabaseMetaData.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getMetaData est spécifiée par la méthode getMetaData dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
