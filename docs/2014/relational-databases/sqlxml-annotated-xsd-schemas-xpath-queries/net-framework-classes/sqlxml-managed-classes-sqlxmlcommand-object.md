---
title: Objet SqlXmlCommand (Classes managées de SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 736345b7ee5b9c3e40f0ae34fe139cb911cad42f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52807341"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a>Objet SqlXmlCommand (classes managées SQLXML)
  Il s’agit du constructeur pour l’objet SqlXmlCommand :  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 Où `cnString` est la chaîne de connexion ADO ou OLEDB qui identifie le serveur, base de données et les informations de connexion-par exemple, `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.  
  
 Dans la chaîne de connexion, le `Provider` doit être SQLOLEDB et le `Data Provider` ne doit pas être inclus dans la chaîne de fournisseur).  
  
 Pour obtenir un exemple fonctionnel, consultez [l’exécution des requêtes SQL &#40;Classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
## <a name="methods"></a>Méthodes  
 TheSqlXmlCommand objet prend en charge plusieurs méthodes, notamment les méthodes suivantes pour exécuter une commande :  
  
 ExecuteNonQuery() void  
 Exécute la commande, mais ne retourne rien. Cette méthode est utile si vous souhaitez exécuter une commande autre qu'une requête (autrement dit, une commande qui ne retourne rien). L'exécution d'un code de mise à jour (updategram) ou d'un DiffGram qui met à jour des enregistrements mais ne retourne rien est un exemple d'une telle méthode.  
  
 ExecuteStream() de Stream  
 Retourne un nouvel objet Stream. Cette méthode est utile lorsque vous souhaitez que les résultats de la requête vous soient retournés dans un nouveau flux de données. Pour obtenir un exemple fonctionnel, consultez [l’exécution des requêtes SQL &#40;Classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 ExecuteToStream void publique (Stream outputStream)  
 Écrit les résultats de la requête dans un flux de données existant. Cette méthode est utile lorsque vous avez un flux auquel vous voulez ajouter (par exemple, pour obtenir les résultats de requête écrites dans le System.Web.HttpResponse.OutputStream) les résultats. Pour obtenir un exemple fonctionnel, consultez [l’exécution des requêtes SQL &#40;Classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 ExecuteXmlReader() de XmlReader  
 Retourne un objet XmlReader. Vous pouvez utiliser cette méthode à manipuler directement les données dans l’objet XmlReader ou incorporer dans l’architecture chainable de System.Xml. Pour plus d'informations, consultez la documentation sur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Pour obtenir un exemple fonctionnel, consultez [l’exécution de requêtes SQL à l’aide de la méthode ExecuteXMLReader](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
 Objet de TheSqlXmlCommand prend également en charge ces méthodes supplémentaires :  
  
 SqlXmlParameter CreateParameter()  
 Crée un objet SqlXmlParameter. Vous pouvez définir des valeurs pour le *nom* et *valeur* paramètres de cet objet. Cette méthode est utile si vous voulez transmettre des paramètres à une commande. Pour obtenir un exemple fonctionnel, consultez [l’exécution des requêtes SQL &#40;Classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 ClearParameters() void  
 Efface le ou les paramètres qui ont été créés pour un objet de commande donné. Cette méthode est utile si vous souhaitez exécuter plusieurs requêtes sur le même objet de commande.  
  
## <a name="properties"></a>Properties  
 L’objet SqlXmlCommand prend également en charge ces propriétés :  
  
 ClientSideXml  
 Si la valeur est True, cela indique que la conversion de l'ensemble de lignes en XML doit se produire sur le client et non pas sur le serveur. Cette propriété s'avère utile si vous souhaitez déplacer la charge de performance vers le niveau intermédiaire. La propriété vous permet également d'imbriquer les procédures stockées existantes avec FOR XML pour obtenir une sortie XML.  
  
 SchemaPath  
 Nom du schéma de mappage avec le chemin d'accès au répertoire (par exemple, C:\x\y\MySchema.xml). Cette propriété est utile pour spécifier un schéma de mappage pour des requêtes XPath. Le chemin d'accès spécifié peut être absolu ou relatif. Si le chemin d’accès est relatif, le chemin d’accès de base qui est spécifié dans le chemin d’accès de Base est utilisé pour résoudre le chemin d’accès relatif. Si aucun chemin d'accès de base n'est spécifié, le chemin d'accès relatif se rapporte au répertoire en cours. Pour obtenir un exemple fonctionnel, consultez [l’accès à des fonctionnalités de SQLXML dans l’environnement .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 XslPath  
 Nom du fichier XSL avec le chemin d'accès au répertoire. Le chemin d'accès spécifié peut être absolu ou relatif. Si le chemin d’accès est relatif, le chemin d’accès de base qui est spécifié dans le chemin d’accès de Base est utilisé pour résoudre le chemin d’accès relatif. Si aucun chemin d'accès de base n'est spécifié, le chemin d'accès relatif se rapporte au répertoire en cours. Pour obtenir un exemple fonctionnel, consultez [appliquer une Transformation XSL &#40;Classes managées SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 Chemin d’accès de base  
 Chemin d'accès de base (chemin d'accès à un répertoire). Cette propriété est utile pour résoudre un chemin relatif est spécifié pour un fichier XSL (en utilisant la xslpath, propriété), un fichier de schéma de mappage (en utilisant la schemapath, propriété) ou une référence de schéma externes dans un modèle XML (spécifié à l’aide de la `mapping-schema` attribut).  
  
 OutputEncoding  
 Spécifie l'encodage pour le flux de données retourné lorsque la commande s'exécute. Cette propriété est utile pour demander un encodage spécifique pour le flux de données retourné. Entre autres, les encodages communément utilisés sont UTF-8, ANSI et Unicode. UTF-8 est l'encodage par défaut.  
  
 Espaces de noms  
 Permet l'exécution de requêtes XPath qui utilisent des espaces de noms. Pour plus d’informations sur les requêtes XPath avec des espaces de noms, consultez [l’exécution de requêtes XPath avec des espaces de noms &#40;Classes managées SQLXML&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md). Pour obtenir un exemple fonctionnel, consultez [l’exécution des requêtes XPath &#40;Classes managées SQLXML&#41;](executing-xpath-queries-sqlxml-managed-classes.md).  
  
 RootTag  
 Fournit l'élément racine unique pour XML généré par l'exécution d'une commande. Un document XML valide requiert une balise de niveau racine unique. Si la commande exécutée génère un fragment XML (sans un élément de premier niveau unique), vous pouvez spécifier un élément racine pour les données XML retournées. Pour obtenir un exemple fonctionnel, consultez [appliquer une Transformation XSL &#40;Classes managées SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 CommandText  
 Texte de la commande. Cette propriété est utilisée pour spécifier le texte de la commande que vous souhaitez exécuter. Pour obtenir un exemple fonctionnel, consultez [l’exécution des requêtes SQL &#40;Classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 CommandStream  
 Flux de commande. Cette propriété est utile si vous souhaitez exécuter une commande à partir d'un fichier (par exemple, un modèle XML). Lorsque vous utilisez CommandStream, uniquement **« Modèle »**, **« UpdateGram »** et **« DiffGram » CommandType** valeurs sont prises en charge. Pour obtenir un exemple fonctionnel, consultez [l’exécution des fichiers de modèle à l’aide de la propriété CommandStream](executing-template-files-by-using-the-commandstream-property.md).  
  
 CommandType  
 Identifie le type de commande. Cette propriété est utilisée pour spécifier le type de commande que vous souhaitez exécuter. Les valeurs du tableau ci-dessous déterminent le type de la commande. Pour obtenir un exemple fonctionnel, consultez [l’accès à des fonctionnalités de SQLXML dans l’environnement .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
|Value|Description|  
|-----------|-----------------|  
|SqlXmlCommandType.Sql|Exécute une commande SQL (par exemple, `SELECT * FROM Employees FOR XML AUTO`).|  
|SqlXmlCommandType.XPath|Exécute une commande XPath (par exemple, `Employees[@EmployeeID=1]`).|  
|SqlXmlCommandType.Template|Exécute un modèle XML.|  
|SqlXmlCommandType.TemplateFile|Exécute un fichier modèle dans le dossier spécifié.|  
|SqlXmlCommandType.UpdateGram|Exécute un code de mise à jour (updategram).|  
|SqlXmlCommandType.Diffgram|Exécute un DiffGram.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlXmlParameter &#40;Classes managées SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)   
 [Objet SqlXmlAdapter &#40;Classes managées SQLXML&#41;](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
