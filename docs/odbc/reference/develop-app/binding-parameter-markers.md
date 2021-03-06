---
title: Liaison des marqueurs de paramètres | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c71967bd72f7f13a725d47517cb9e66eee7da87f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645987"
---
# <a name="binding-parameter-markers"></a>Liaison de marqueurs de paramètre
L’application lie les paramètres en appelant **SQLBindParameter**. **SQLBindParameter** lie un paramètre à la fois. Avec elle, l’application spécifie les éléments suivants :  
  
-   Le numéro de paramètre. Les paramètres sont numérotés dans l’ordre croissant des paramètres dans l’instruction SQL, en commençant par le numéro 1. Bien qu’il soit juridique pour spécifier un numéro de paramètre est supérieur au nombre de paramètres dans l’instruction SQL, la valeur du paramètre sera ignorée lorsque l’instruction est exécutée.  
  
-   Le type de paramètre (entrée, entrée/sortie ou de sortie). À l’exception des paramètres dans les appels de procédure, tous les paramètres sont des paramètres d’entrée. Pour plus d’informations, consultez [paramètres de procédure](../../../odbc/reference/develop-app/procedure-parameters.md), plus loin dans cette section.  
  
-   Le C type, l’adresse et octets longueur des données de la variable liée au paramètre. Le pilote doit être en mesure de convertir les données à partir du type de données C au type de données SQL ou une erreur est retournée. Pour une liste des conversions prises en charge, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) annexe d : Types de données.  
  
-   Le type de données SQL, la précision et l’échelle du paramètre lui-même.  
  
-   L’adresse d’une mémoire tampon de longueur / d’indicateur. Il fournit la longueur d’octet de données binaires ou caractères, spécifie que les données sont NULL ou indique que les données sont envoyées avec **SQLPutData**. Pour plus d’informations, consultez [à l’aide des valeurs de longueur / d’indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Par exemple, le code suivant lie *vendeur* et *CustID* aux paramètres pour les colonnes vendeur et CustID. Étant donné que *vendeur* contient des données caractères, ce qui est de longueur variable, le code spécifie la longueur d’octet *vendeur* (11) et lie *SalesPersonLenOrInd* à contient la longueur d’octet des données dans *vendeur*. Ces informations ne sont pas nécessaires pour *CustID* , car il contient des données de type entier, ce qui est de longueur fixe.  
  
```  
SQLCHAR       SalesPerson[11];  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLUINTEGER   CustID;  
  
// Bind SalesPerson to the parameter for the SalesPerson column and  
// CustID to the parameter for the CustID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,  
                  SalesPerson, sizeof(SalesPerson), &SalesPersonLenOrInd);  
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &CustID, 0, &CustIDInd);  
  
// Set values of salesperson and customer ID and length/indicators.  
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");  
SalesPersonLenOrInd = SQL_NTS;  
CustID = 1331;  
CustIDInd = 0;  
  
// Execute a statement to get data for all orders made to the specified  
// customer by the specified salesperson.  
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);  
```  
  
 Lorsque **SQLBindParameter** est appelée, le pilote stocke ces informations dans la structure de l’instruction. Lorsque l’instruction est exécutée, elle utilise les informations à récupérer les données de paramètre et les envoyer à la source de données.  
  
> [!NOTE]  
>  Dans ODBC 1.0, les paramètres ont été liés avec **SQLSetParam**. Le Gestionnaire de pilotes mappe les appels entre **SQLSetParam** et **SQLBindParameter**, selon les versions d’ODBC utilisée par l’application et le pilote.
