---
title: Configuration d’erreur pour le Cube, Partition et le traitement de Dimension (SSAS - multidimensionnel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.cubeproperties.errorconfiguration.f1
- sql12.asvs.sqlserverstudio.dimensionproperties.errorconfiguration.f1
- sql12.asvs.sqlserverstudio.partitionproperties.errorconfiguration.f1
ms.assetid: 3f442645-790d-4dc8-b60a-709c98022aae
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ec0d1acbe1714159d6777f6cb91056e4e14b356
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175369"
---
# <a name="error-configuration-for-cube-partition-and-dimension-processing-ssas---multidimensional"></a>Configuration d'erreur pour le traitement des cubes, des partitions et des dimensions (SSAS - Multidimensionnel)
  Les propriétés de configuration d'erreur sur les objets cube, partition ou de dimension déterminent le mode de réponse du serveur lorsqu'une erreur d'intégrité des données se produit pendant le traitement. Les clés dupliquées, manquantes et les valeurs NULL dans une colonne clé déclenchent généralement ces erreurs, et comme l'enregistrement à l'origine de l'erreur n'est pas ajouté à la base de données, vous pouvez définir des propriétés qui déterminent ce qui se produit après. Par défaut, le traitement s'arrête. Cependant, lorsque vous développez le cube, vous pouvez souhaiter que le traitement continue lorsque des erreurs se produisent afin de tester le comportement du cube avec des données importées, même si elles sont incomplètes.  
  
 Cette rubrique comprend les sections suivantes :  
  
-   [Ordre d’exécution](#bkmk_exec)  
  
-   [Comportements par défaut](#bkmk_default)  
  
-   [Propriétés de configuration d'erreur](#bkmk_props)  
  
-   [Emplacement de définition des propriétés de configuration d'erreur](#bkmk_tools)  
  
-   [Clés manquantes (KeyNotFound)](#bkmk_missing)  
  
-   [Clés étrangères NULL dans une table de faits (KeyNotFound)](#bkmk_nullfact)  
  
-   [Clés NULL dans une dimension](#bkmk_nulldim)  
  
-   [Clés dupliquées résultant de relations incohérentes (KeyDuplicate)](#bkmk_dupe)  
  
-   [Modifier le nombre maximal d'erreurs ou l'action lorsque le nombre maximal d'erreurs est atteint](#bkmk_limit)  
  
-   [Définir le chemin d'accès du journal des erreurs](#bkmk_log)  
  
-   [Étape suivante](#bkmk_next)  
  
##  <a name="bkmk_exec"></a> Ordre d’exécution  
 Le serveur exécute toujours `NullProcessing` avant les règles `ErrorConfiguration` règles pour chaque enregistrement. Il est important de comprendre cela, car les propriétés de traitement Null qui convertissent les valeurs Null en zéros peuvent introduire des erreurs de clé dupliquée lorsque plusieurs enregistrements d'erreur contiennent un zéro dans une colonne clé.  
  
##  <a name="bkmk_default"></a> Comportements par défaut  
 Par défaut, le traitement s'arrête à la première erreur impliquant une colonne clé. Ce comportement est contrôlé par un nombre maximal d'erreurs qui spécifie zéro comme nombre d'erreurs autorisées et la directive Arrêter le traitement qui indique au serveur d'arrêter le traitement lorsque le nombre d'erreurs est atteint.  
  
 Les enregistrements qui déclenchent une erreur, en raison de valeurs NULL, manquantes ou dupliquées, sont convertis en membre inconnu ou ignorés. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] n’importe pas les données qui ne respectent pas les contraintes d’intégrité des données.  
  
-   Conversion en membre inconnu se produit par défaut, en raison du `ConvertToUnknown` définition pour `KeyErrorAction`. Les enregistrements alloués à un membre inconnu sont mis en quarantaine dans la base de données en tant que preuve d'un problème que vous pouvez examiner une fois le traitement terminé.  
  
     Membres inconnus sont exclus des charges de travail de requête, mais ils seront visibles dans certaines applications clientes si le `UnknownMember` a la valeur **Visible**.  
  
     Pour effectuer le suivi du nombre de valeurs NULL converties en membre inconnu, modifiez la propriété `NullKeyConvertedToUnknown` de façon à consigner ces erreurs dans le journal ou dans la fenêtre de traitement.  
  
-   Est ignoré lorsque vous définissez manuellement la `KeyErrorAction` propriété `DiscardRecord`.  
  
 Les propriétés de configuration d'erreur permettent de déterminer le mode de réponse du serveur lorsqu'une erreur se produit. Les options sont l'arrêt immédiat du traitement, la poursuite du traitement mais l'arrêt de la journalisation ou la poursuite du traitement et de la journalisation des erreurs. Les valeurs par défaut varient en fonction de la gravité de l'erreur.  
  
 Le nombre d'erreurs assure le suivi du nombre d'erreurs qui se produisent. Lorsque vous définissez une limite supérieure, la réponse du serveur change lorsque cette limite est atteinte. Par défaut, le serveur arrête le traitement une fois la limite atteinte. Le nombre maximal par défaut est 0, ce qui entraîne l'arrêt du traitement lors de la première erreur.  
  
 Les erreurs ayant un impact élevé, notamment une clé manquante ou une valeur NULL dans un champ clé, doivent être traitées rapidement. Par défaut, ces erreurs adhèrent aux `ReportAndContinue` des comportements de serveur, où le serveur intercepte l’erreur, il ajoute au nombre d’erreurs, puis continue le traitement (sauf si le nombre maximal d’erreurs est zéro, et le traitement s’arrête immédiatement).  
  
 D'autres erreurs sont générées, mais pas comptabilisées ou consignées par défaut (paramètre `IgnoreError`), car l'erreur ne pose pas nécessairement un problème d'intégrité des données.  
  
 Le nombre d'erreurs est attribué par les paramètres de traitement des valeurs NULL. Pour les attributs de dimension, les options de traitement des valeurs NULL déterminent le mode de réponse du serveur lorsqu'aucune valeur NULL n'est rencontrée. Par défaut, les valeurs NULL dans une colonne numérique sont converties en zéros, tandis que les valeurs NULL dans une colonne de chaîne sont traitées en tant que chaînes vides. Remplacez les propriétés `NullProcessing` de façon à intercepter les valeurs NULL avant qu'elles ne soient converties en erreurs `KeyNotFound` ou `KeyDuplicate`. Pour plus d’informations, consultez [Clés NULL dans une dimension](#bkmk_nulldim) .  
  
 Les erreurs sont consignées dans la boîte de dialogue Traiter, mais ne sont pas enregistrées. Vous pouvez spécifier un nom de fichier journal d'erreurs de clé pour collecter les erreurs dans un fichier texte.  
  
##  <a name="bkmk_props"></a> Propriétés de configuration d'erreur  
 Il existe neuf propriétés de configuration d'erreur. Cinq sont utilisées pour déterminer la réponse du serveur lorsqu'une erreur spécifique se produit. Les quatre autres concernent les charges de travail de configuration d'erreur, telles que le nombre d'erreurs à autoriser, l'action à entreprendre lorsque le nombre maximal d'erreurs est atteint et s'il faut collecter les erreurs dans un fichier journal.  
  
 **Réponse du serveur à des erreurs spécifiques**  
  
|Propriété|Valeur par défaut|Autres valeurs|  
|--------------|-------------|------------------|  
|`CalculationError`<br /><br /> Se produit lors de l'initialisation de la configuration d'erreur.|`IgnoreError` journaux ni comptabilise l’erreur ; le traitement continue tant que le nombre d’erreurs est inférieur au nombre maximal.|`ReportAndContinue` consigne et comptabilise l’erreur.<br /><br /> `ReportAndStop` signale l’erreur et arrête le traitement immédiatement, quel que soit le nombre maximal d’erreurs.|  
|`KeyNotFound`<br /><br /> Se produit lorsqu'une clé étrangère dans une table de faits n'a pas de clé primaire correspondante dans une table de dimension associée (par exemple, une table de faits Sales contient in enregistrement avec un ID de produit qui n'existe pas dans la table de dimension Product). Cette erreur se produit lors du traitement des partitions, ou du traitement des dimensions en flocons.|`ReportAndContinue` consigne et comptabilise l’erreur.|`ReportAndStop` signale l’erreur et arrête le traitement immédiatement, quel que soit le nombre maximal d’erreurs.<br /><br /> `IgnoreError` journaux ni comptabilise l’erreur ; le traitement continue tant que le nombre d’erreurs est inférieur au nombre maximal. Les enregistrements qui déclenchent cette erreur sont convertis en membre inconnu par défaut, mais vous pouvez modifier la propriété `KeyErrorAction` de façon à les ignorer.|  
|`KeyDuplicate`<br /><br /> Se produit lorsque des clés d'attribut en double sont détectées dans une dimension. Dans la plupart des cas, il est possible de disposer de clés d'attribut dupliquées, mais cette erreur vous informe des doublons afin que vous puissiez rechercher dans la dimension les erreurs de conception qui peuvent entraîner des relations incohérentes entre les attributs.|`IgnoreError` journaux ni comptabilise l’erreur ; le traitement continue tant que le nombre d’erreurs est inférieur au nombre maximal.|`ReportAndContinue` consigne et comptabilise l’erreur.<br /><br /> `ReportAndStop` signale l’erreur et arrête le traitement immédiatement, quel que soit le nombre maximal d’erreurs.|  
|`NullKeyNotAllowed`<br /><br /> Se produit lorsque `NullProcessing`  =  `Error` est défini sur un attribut de dimension ou lorsque les valeurs null existent dans une colonne clé d’attribut utilisée pour identifier un membre.|`ReportAndContinue` consigne et comptabilise l’erreur.|`ReportAndStop` signale l’erreur et arrête le traitement immédiatement, quel que soit le nombre maximal d’erreurs.<br /><br /> `IgnoreError` journaux ni comptabilise l’erreur ; le traitement continue tant que le nombre d’erreurs est inférieur au nombre maximal. Les enregistrements qui déclenchent cette erreur sont convertis en membre inconnu par défaut, mais vous pouvez définir le `KeyErrorAction` propriété à les ignorer.|  
|`NullKeyConvertedToUnknown`<br /><br /> Se produit lorsque des valeurs NULL sont, par la suite, converties en membre inconnu. Paramètre `NullProcessing`  =  `ConvertToUnknown` sur une dimension attribut déclenche cette erreur.|`IgnoreError` journaux ni comptabilise l’erreur ; le traitement continue tant que le nombre d’erreurs est inférieur au nombre maximal.|Pour afficher cette erreur à titre d'information, conservez la valeur par défaut. Sinon, vous choisissez `ReportAndContinue` de façon à signaler l'erreur dans la fenêtre de traitement et la comptabiliser dans le nombre maximal d'erreurs.<br /><br /> `ReportAndStop` signale l’erreur et arrête le traitement immédiatement, quel que soit le nombre maximal d’erreurs.|  
  
 **Propriétés générales**  
  
|**Propriété**|**Valeurs**|  
|------------------|----------------|  
|`KeyErrorAction`|L’action effectuée par le serveur quand un `KeyNotFound` erreur se produit. Réponses valides à cette erreur sont `ConvertToUnknown` ou `DiscardRecord`.|  
|`KeyErrorLogFile`|Il s'agit d'un nom de fichier défini par l'utilisateur qui doit avoir une extension de fichier .log, situé dans un dossier sur lequel le compte de services dispose des autorisations d'accès en lecture/écriture. Ce fichier journal contient uniquement les erreurs générées lors du traitement. Utilisez la Boîte noire si vous avez besoin de plus d'informations.|  
|`KeyErrorLimit`|Il s'agit du nombre maximal d'erreurs d'intégrité des données que le serveur autorise avant que le traitement échoue. Une valeur égale à -1 indique un nombre illimité. La valeur par défaut est 0, ce qui signifie que le traitement s'arrête après la première erreur. Vous pouvez également définir un nombre entier.|  
|`KeyErrorLimitAction`|Il s'agit de l'action entreprise par le serveur lorsque le nombre maximal d'erreurs de clé est atteint. Avec **Arrêter le traitement**, le traitement se termine immédiatement. Avec **Arrêter l’enregistrement dans le journal**, le traitement continue, mais les erreurs ne sont plus signalées ou comptabilisées.|  
  
##  <a name="bkmk_tools"></a> Emplacement de définition des propriétés de configuration d'erreur  
 Utilisez les pages de propriétés dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] après avoir déployé la base de données, ou dans le projet de modèle dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Les mêmes propriétés sont disponibles dans les deux outils. Vous pouvez également définir des propriétés de configuration erreur dans le fichier msmdrsrv.ini pour modifier les paramètres par défaut du serveur de configuration d’erreur et `Batch` et `Process` commandes si le traitement s’exécute en tant qu’une opération de script.  
  
 Vous pouvez définir la configuration d'erreur sur n'importe quel objet pouvant être traité en tant qu'opération autonome.  
  
#### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
  
1.  Dans l’Explorateur d’objets, cliquez sur **Propriétés** , puis sur l’un de ces objets : dimension, cube ou partition.  
  
2.  Dans Propriétés, cliquez sur **Configuration d’erreur**.  
  
#### <a name="sql-server-data-tools"></a>SQL Server Data Tools  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur une dimension ou sur un cube. `ErrorConfiguration` apparaît dans les propriétés dans le volet inférieur.  
  
2.  Sinon, pour une seule dimension, cliquez sur la dimension dans l’Explorateur de solutions, sélectionnez `Process`, puis choisissez **modifier les paramètres** dans la boîte de dialogue traiter la Dimension. Les options de configuration d'erreur s'affichent dans l'onglet Erreurs de clé de dimension.  
  
##  <a name="bkmk_missing"></a> Clés manquantes (KeyNotFound)  
 Les enregistrements avec une valeur de clé manquante ne sont pas ajoutés à la base de données, même lorsque les erreurs sont ignorées ou le nombre d'erreurs est illimité.  
  
 Le serveur génère le `KeyNotFound` erreur lors du traitement de partition, lorsqu’un enregistrement de table de faits contient une valeur de clé étrangère, mais la clé étrangère n’a aucun enregistrement correspondant dans une table de dimension associées. Cette erreur se produit également lors du traitement des tables de dimension associées ou en flocons, où un enregistrement dans une dimension spécifie une clé étrangère qui n'existe pas dans la dimension associée.  
  
 Lorsqu'une erreur `KeyNotFound` se produit, l'enregistrement incriminé est alloué au membre inconnu. Ce comportement est contrôlé par le **Action clé**, dont la valeur `ConvertToUnknown`, de sorte que vous pouvez afficher les enregistrements alloués à un examen approfondi.  
  
##  <a name="bkmk_nullfact"></a> Clés étrangères NULL dans une table de faits (KeyNotFound)  
 Par défaut, une valeur NULL dans une colonne clé étrangère d'une table de faits est convertie en zéro. En supposant que zéro n'est pas une valeur de clé étrangère valide, une erreur `KeyNotFound` est consignée et comptabilisée dans le nombre maximal d'erreurs qui est zéro par défaut.  
  
 Pour autoriser la poursuite du traitement, vous pouvez gérer la valeur NULL avant conversion et recherche des erreurs. Pour ce faire, définissez `NullProcessing` à `Error`.  
  
#### <a name="set-nullprocessing-property-on-a-measure"></a>Définir la propriété NullProcessing sur une mesure  
  
1.  Dans SQL Server Data Tools, dans l'Explorateur de solutions, double-cliquez sur un cube pour l'ouvrir dans le Concepteur de cube.  
  
2.  Cliquez avec le bouton droit sur une mesure dans le volet Mesures et choisissez **Propriétés**.  
  
3.  Dans Propriétés, développez **Source** pour afficher `NullProcessing` propriété. Elle a la valeur **Automatic** par défaut qui, pour les éléments OLAP, convertit les valeurs NULL en zéros pour les champs contenant des données numériques.  
  
4.  Remplacez la valeur par `Error` à exclure tous les enregistrements ayant une valeur null, ce qui évite la conversion null numériques (zéros). Cette modification vous permet d’éviter des erreurs de clé dupliquée reliés à plusieurs enregistrements contenant un zéro dans la colonne clé et également éviter `KeyNotFound` erreurs lorsqu’une clé étrangère de valeur zéro ne possède aucune clé primaire équivalente dans une table de dimension associée.  
  
##  <a name="bkmk_nulldim"></a> Clés NULL dans une dimension  
 Pour continuer le traitement lorsque les valeurs null sont détectées dans les clés étrangères dans une dimension en flocons, gérez tout d’abord les valeurs null en définissant `NullProcessing` sur la `KeyColumn` de l’attribut de dimension. Cela permet d'ignorer ou de convertir l'enregistrement, avant que l'erreur `KeyNotFound` ne se produise.  
  
 Vous avez deux options de gestion des valeurs NULL sur l'attribut de dimension :  
  
-   Définissez `NullProcessing` = `UnknownMember` pour allouer les enregistrements avec des valeurs null au membre inconnu. Cela génère une erreur `NullKeyConvertedToUnknown`, qui est ignorée par défaut.  
  
-   Définissez `NullProcessing` = `Error` pour exclure les enregistrements avec des valeurs null. Cette opération génère le `NullKeyNotAllowed` erreur, ce qui est connecté et des nombres dans le nombre maximal d’erreurs de clé. Vous pouvez définir la propriété de configuration d’erreur sur **clé Null non autorisée** à `IgnoreError` pour permettre la poursuite du traitement.  
  
 Les valeurs NULL peuvent poser des problèmes pour les champs non-clé. De fait, les requêtes MDX retournent un résultat différent si la valeur NULL est interprétée en tant que zéro ou chaîne vide. C'est pourquoi, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit des options de traitement des valeurs NULL qui vous permettent de prédéfinir le comportement de conversion souhaité. Consultez [définition du membre inconnu et les propriétés de traitement Null](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md) et <xref:Microsoft.AnalysisServices.NullProcessing> pour plus d’informations.  
  
#### <a name="set-nullprocessing-property-on-a-dimension-attribute"></a>Définir la propriété NullProcessing sur un attribut de dimension  
  
1.  Dans SQL Server Data Tools, dans l'Explorateur de solutions, double-cliquez sur une dimension pour l'ouvrir dans le Concepteur de dimension.  
  
2.  Cliquez avec le bouton droit sur un attribut dans le volet Attributs et choisissez **Propriétés**.  
  
3.  Dans Propriétés, développez **KeyColumns** pour afficher `NullProcessing` propriété. Elle a la valeur **Automatic** par défaut, qui convertit les valeurs NULL en zéros pour les champs contenant des données numériques. Modifiez la valeur en `Error` ou `UnknownMember`.  
  
     Cette modification supprime les conditions sous-jacentes qui déclenchent `KeyNotFound` en ignorant ou en convertissant l’enregistrement avant qu’il est vérifié pour les erreurs.  
  
     Selon la configuration d'erreur, ces actions entraînent une erreur qui est signalée et comptabilisée. Vous devrez peut-être modifier d’autres propriétés, telles que la définition `KeyNotFound` à `ReportAndContinue` ou `KeyErrorLimit` à une valeur différente de zéro, pour permettre le traitement continue lorsque ces erreurs sont signalées et comptabilisées.  
  
##  <a name="bkmk_dupe"></a> Clés dupliquées résultant de relations incohérentes (KeyDuplicate)  
 Par défaut, la présence d'une valeur de clé dupliquée n'arrête pas le traitement, mais l'erreur est ignorée et l'enregistrement en double est exclu de la base de données.  
  
 Pour modifier ce comportement, définissez `KeyDuplicate` à `ReportAndContinue` ou `ReportAndStop` pour signaler l’erreur. Vous pourrez ensuite examiner l'erreur pour déterminer les failles potentielles dans la conception de la dimension.  
  
##  <a name="bkmk_limit"></a> Modifier le nombre maximal d'erreurs ou l'action lorsque le nombre maximal d'erreurs est atteint  
 Vous pouvez augmenter le nombre maximal d'erreurs pour permettre plus d'erreurs lors du traitement. Il n'y a aucune indication pour augmenter le nombre maximal d'erreurs ; la valeur appropriée varie selon votre scénario. Limites d’erreur sont spécifiés en tant que `KeyErrorLimit` dans `ErrorConfiguration` propriétés dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ou en tant que **nombre d’erreurs** dans l’onglet Configuration d’erreur des propriétés des dimensions, cubes ou groupes de mesures dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Une fois le nombre maximal d'erreurs atteint, spécifiez que le traitement s'arrête ou que l'enregistrement dans le journal s'arrête. Par exemple, supposons que vous définissez l’action sur `StopLogging` sur un nombre maximal d’erreurs de 100. À la 101è erreur, le traitement continue, mais les erreurs ne sont plus consignées ou comptabilisées. Actions de limite d’erreur sont spécifiées en tant que `KeyErrorLimitAction` dans `ErrorConfiguration` propriétés dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ou en tant que **sur l’action pour l’erreur** dans l’onglet Configuration d’erreur des propriétés des dimensions, cubes ou groupes de mesures dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
##  <a name="bkmk_log"></a> Définir le chemin d'accès du journal des erreurs  
 Vous pouvez spécifier un fichier pour stocker les messages d'erreur associés aux clés qui sont signalés lors du traitement. Par défaut, les erreurs sont visibles pendant le traitement interactif dans la fenêtre Traiter, puis ignorées si vous fermez la fenêtre ou la session. Le journal contient uniquement les informations d'erreur associées aux clés, identiques aux erreurs signalées dans les boîtes de dialogue de traitement.  
  
 Les erreurs sont enregistrées dans un fichier texte et il doit avoir une extension de fichier .log. Le fichier est vide sauf si des erreurs se produisent. Par défaut, un fichier est créé dans le dossier DATA. Vous pouvez spécifier un autre dossier tant que le compte de service Analysis Services peut écrire à cet emplacement.  
  
##  <a name="bkmk_next"></a> Étape suivante  
 Décidez si les erreurs arrêtent le traitement ou sont ignorées. N'oubliez pas que seule l'erreur est ignorée. L'enregistrement ayant provoqué l'erreur n'est pas ignoré ; il est annulé ou converti en membre inconnu. Les enregistrements qui ne sont pas conformes aux règles d'intégrité des données ne sont jamais ajoutés à la base de données. Par défaut, le traitement s'arrête lorsqu'la première erreur se produit, mais vous pouvez modifier ce comportement en augmentant le nombre maximal d'erreurs. Dans le développement de cube, il peut être utile d'abaisser les règles de configuration d'erreur, ce qui autorise la poursuite du traitement, de façon à ce qu'il y ait des données à tester.  
  
 Décidez s'il faut modifier les comportements de traitement des valeurs NULL par défaut. Par défaut, les valeurs NULL dans une colonne de chaîne sont traitées en tant que valeurs vides, alors que les valeurs NULL dans une colonne numérique sont traitées en tant que zéro. Pour obtenir des instructions sur la définition du traitement de la valeur NULL sur un attribut, consultez [Définition du membre inconnu et des propriétés de traitement Null](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés du journal](../server-properties/log-properties.md)   
 [Définition du membre inconnu et des propriétés de traitement Null](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
  
  
