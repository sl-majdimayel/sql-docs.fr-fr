---
title: Applet de commande Remove-RoleMember | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e38f56ab-facd-4bef-9502-f52f8486a6a6
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c093787d86398acaaeaca8f282e1f588c3e726d7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="remove-rolemember-cmdlet"></a>Applet de commande Remove-RoleMember

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Supprimez un membre du rôle spécifié d'une base de données Analysis Services.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
## <a name="syntax"></a>Syntaxe  
 `Remove-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Remove-RoleMember [-DatabaseRole] <Microsoft.AnalysisServices.Role> [-MemberName] <System.String>  [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 L'applet de commande Remove-RoleMember supprime un membre existant d'un rôle d'une base de données Analysis Services.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-membername-string"></a>-MemberName \<chaîne >  
 Spécifie l'utilisateur ou le groupe Windows à supprimer du rôle.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-database-string"></a>-De base de données \<chaîne >  
 Spécifie la base de données à laquelle le rôle appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-rolename-string"></a>-RoleName \<chaîne >  
 Spécifie le rôle duquel vous supprimez des membres.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-databaserole-string"></a>-DatabaseRole \<chaîne >  
 Spécifie l'objet Microsoft.AnalysisServices.Role duquel le membre est supprimé. Utilisez ce paramètre comme une alternative aux paramètres –Database et –RoleName, lorsque vous souhaitez fournir le rôle de base de données via le pipeline.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true (ByPropertyName)|  
|Accepter les caractères génériques ?|false|  
  
### <a name="commonparameters"></a>\<Paramètres_courants >  
 La commande cmdlet prend en charge les paramètres communs : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Aucun.  
  
## <a name="example-1"></a>Exemple 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Cette commande supprime un compte d'utilisateur de domaine Windows du rôle Lecteur pour la base de données AdventureWorks exécutée sur une instance par défaut locale.  
  
## <a name="example-2"></a>Exemple 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> remove-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 La ligne 1 ajoute tous les rôles de la base de données AWTEST au pipeline. La ligne 2, où vous tapez $roles à l'invite, affiche le tableau de rôles. La ligne 3 supprime l'utilisateur Windows « adventure-works\bobh » du premier rôle dans le tableau.  
  
## <a name="example-3"></a>Exemple 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Remove-rolemember –membername “adventure-works\bobh”  
```  
  
 Cette commande supprime un compte d'utilisateur de domaine Windows du premier rôle dans un tableau, où le tableau est créé en répertoriant les enfants du dossier Rôles, dans le contexte d'une base de données spécifique (AWTEST).  
  

  
  