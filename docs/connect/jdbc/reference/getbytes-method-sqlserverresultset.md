---
title: GetBytes, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d16a0aea-6144-4fcb-bcbc-5d7daa36d327
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc51a4cb3680952c294f03718232b9571108a469
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741987"
---
# <a name="getbytes-method-sqlserverresultset"></a>Méthode getBytes (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de la colonne désignée dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant que tableau **d’octets** dans le langage de programmation Java.  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Nom   |Description|  
|----------|-----------------|  
|[getBytes (int)](../../../connect/jdbc/reference/getbytes-method-int-sqlserverresultset.md)|Récupère la valeur de l’index de la colonne désignée dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant que tableau **d’octets** dans le langage de programmation Java.|  
|[getBytes (java.lang.String)](../../../connect/jdbc/reference/getbytes-method-java-lang-string-sqlserverresultset.md)|Récupère la valeur du nom de colonne désigné dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant que tableau **d’octets** dans le langage de programmation Java.|  
  
## <a name="remarks"></a>Notes   
 Dans la version précédente du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerResultSet.getBytes pour convertir des valeurs entre des tableaux d’octets et le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
