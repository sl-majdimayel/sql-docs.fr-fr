---
title: ActiveCommand, propriété-Exemple (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ActiveCommand property [ADO], Visual Basic example
ms.assetid: 23b06499-62df-4f46-88eb-6da392f9b456
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a45eafed2c0e673820a5b93eaa13438ac7898988
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617147"
---
# <a name="activecommand-property-example-vb"></a>ActiveCommand, exemple de propriété (VB)
Cet exemple montre la [ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md) propriété.  
  
 Une sous-routine un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) de l’objet dont la propriété **ActiveCommand** propriété est utilisée pour afficher le texte de la commande et le paramètre qui a créé le **Recordset**.  
  
```  
'BeginActiveCommandVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
        'recordset and connection variables  
    Dim cmd As ADODB.Command  
    Dim rst As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
        'record variables  
    Dim strPrompt As String  
    Dim strName As String  
  
    Set Cnxn = New ADODB.Connection  
    Set cmd = New ADODB.Command  
  
    strPrompt = "Enter an author's name (e.g., Ringer): "  
    strName = Trim(InputBox(strPrompt, "ActiveCommandX Example"))  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
  
        'create SQL command string  
    cmd.CommandText = "SELECT * FROM Authors WHERE au_lname = ?"  
    cmd.Parameters.Append cmd.CreateParameter("LastName", adChar, adParamInput, 20, strName)  
  
    Cnxn.Open strCnxn  
    cmd.ActiveConnection = Cnxn  
  
        'create the recordset by executing command string  
    Set rst = cmd.Execute(, , adCmdText)  
        'see the results  
    Call ActiveCommandXprint(rst)  
  
    ' clean up  
    Cnxn.Close  
    Set rst = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndActiveCommandVB  
```  
  
 Le **ActiveCommandXprint** routine reçoit uniquement un **Recordset** de l’objet, mais elle doit imprimer le texte de la commande et le paramètre créé le **Recordset**. Cela est possible, car le **Recordset** l’objet **ActiveCommand** propriété produit associé [commande](../../../ado/reference/ado-api/command-object-ado.md) objet.  
  
 Le **commande** l’objet [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété génère la commande paramétrable qui a créé le **Recordset**. Le **commande** l’objet [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection génère la valeur qui a été remplacée par un espace réservé de paramètre de la commande («**?**»).  
  
 Enfin, un message d’erreur ou son nom et l’ID sont imprimés.  
  
```  
'BeginActiveCommandPrintVB  
Public Sub ActiveCommandXprint(rstp As ADODB.Recordset)  
  
    Dim strName As String  
  
    strName = rstp.ActiveCommand.Parameters.Item("LastName").Value  
  
    Debug.Print "Command text = '"; rstp.ActiveCommand.CommandText; "'"  
    Debug.Print "Parameter = '"; strName; "'"  
  
    If rstp.BOF = True Then  
       Debug.Print "Name = '"; strName; "', not found."  
    Else  
       Debug.Print "Name = '"; rstp!au_fname; " "; rstp!au_lname; _  
             "', author ID = '"; rstp!au_id; "'"  
    End If  
  
    rstp.Close  
    Set rstp = Nothing  
End Sub  
'EndActiveCommandPrintVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveCommand, propriété (ADO)](../../../ado/reference/ado-api/activecommand-property-ado.md)   
 [Objet Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
