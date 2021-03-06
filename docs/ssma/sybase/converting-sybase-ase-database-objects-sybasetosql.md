---
title: Convertir des objets de base de données ASE Sybase (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Converting Database Objects
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3734c2efaaefae44a17381cab46029f2d57666a4
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418160"
---
# <a name="converting-sap-ase-database-objects-sybasetosql"></a>Convertir des objets de base de données SAP ASE (SybaseToSQL)
Après vous être connecté à SAP Adaptive Server Enterprise (ASE), connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure et définir le projet et les options de mappage de données, vous pouvez convertir des objets de base de données SAP Adaptive Server Enterprise (ASE) à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure objets.  
  
## <a name="the-conversion-process"></a>Le processus de conversion  
Convertir des objets de base de données accepte les définitions d’objets à partir de l’ASE, les convertit en similaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure objets et charge ensuite ces informations dans les métadonnées SSMA. Il ne charge pas les informations dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous pouvez ensuite afficher les objets et leurs propriétés à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure.
  
Lors de la conversion, SSMA imprime les messages de sortie pour les messages d’erreur et de volet de sortie pour le **liste d’erreurs** volet. Utilisez les informations de sortie et d’erreur pour déterminer si vous devez modifier vos bases de données ASE ou votre processus de conversion pour obtenir les résultats de la conversion souhaitée.  
  
## <a name="setting-conversion-options"></a>Définition des options de conversion  
Avant de convertir des objets, passez en revue les options de conversion de projet dans le **paramètres du projet** boîte de dialogue. À l’aide de cette boîte de dialogue, vous pouvez définir comment SSMA convertit les fonctions et variables globales. Pour plus d’informations, consultez [paramètres du projet &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
## <a name="converting-ase-database-objects"></a>Convertir des objets de base de données ASE  
Pour convertir des objets de base de données ASE, tout d’abord sélectionner les objets que vous souhaitez convertir et puis SSMA effectuer la conversion. Pour afficher les messages de sortie pendant la conversion, sur le **vue** menu, sélectionnez **sortie**.  
  
**Pour convertir des objets de l’ASE à la syntaxe SQL Server ou SQL Azure**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, développez le serveur de l’ASE, puis puis **bases de données**.  
  
2.  Sélectionnez les objets à convertir :  
  
    -   Pour convertir toutes les bases de données, sélectionnez la case à cocher à côté **bases de données**.  
  
    -   Pour convertir ou omettre une base de données, activez ou désactivez la case à cocher en regard du nom de la base de données.  
  
    -   Pour convertir ou omettre les schémas individuels, développez la base de données, puis **schémas**, puis sélectionnez ou désactivez la case à cocher en regard du schéma.  
  
    -   Pour convertir ou omettre une catégorie d’objets, développez le schéma, puis sélectionnez ou désactivez la case à cocher en regard de la catégorie.  
  
    -   Pour convertir ou omettre des objets, développez le dossier de catégorie, puis sélectionnez ou désactivez la case à cocher en regard de l’objet.  
  
3.  Pour convertir tous les objets sélectionnés, cliquez sur **bases de données**, puis sélectionnez **convertir le schéma**.  
  
    Vous pouvez également convertir des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son conteneur, puis en sélectionnant **convertir le schéma**.  
  
> [!NOTE]  
> Certaines des fonctions système SAP ASE ne correspondent pas exactement les fonctions de système de SQL Server équivalentes dans le comportement. Pour émuler le comportement de SAP ASE, SSMA génère des fonctions définies par l’utilisateur dans la base de données SQL Server converti sous un schéma nommé « s2ss ». Selon les paramètres de projet, certaines fonctions système SQL Server sont remplacées par ces fonctions émulées. SSMA crée les fonctions définies par l’utilisateur suivantes :  
  
||||  
|-|-|-|  
|**char_length_nvarchar**|**index_colorder**|**ssma_datepart**|  
|**char_length_varchar**|**inttohex**|**substring_nvarchar**|  
|**charindex_nvarchar**|**ssma_datediff**|**substring_varbinary**|  
|**charindex_varchar**|**hextoint**|**substring_varchar**|  
|**ulowsurr**|**to_unichar**|**ssma_current_time**|  
|**uhighsurr**|||  
  
## <a name="objects-not-supported-in-azure-sql"></a>Objets non pris en charge dans SQL Azure  
Les mots clés de T-SQL suivants sont utilisés par SSMA pour SAP ASE lors de la conversion vers SQL Server locale, mais ces mots clés ne sont pas pris en charge par la syntaxe T-SQL de SQL Azure :  
  
||||  
|-|-|-|  
|CHECKPOINT|CREATE/ALTER/DROP DEFAULT|CREATE/DROP RULE|  
|DBCC TRACEOFF|DBCC TRACEON|ALL GRANT/REVOKE/DENY|  
|KILL|READTEXT|SELECT INTO|  
|SET OFFSETS|SETUSER|SHUTDOWN|  
|WRITETEXT|||  
  
## <a name="viewing-conversion-problems"></a>Affichage des problèmes de conversion  
Certains objets SAP ASE ne peuvent pas convertir. Vous pouvez déterminer le taux de réussite de la conversion en affichant le rapport de synthèse de conversion.  
  
**Pour afficher un rapport de synthèse**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, sélectionnez **bases de données**.  
  
2.  Dans le volet droit, sélectionnez le **rapport** onglet.  
  
    Ce rapport affiche le rapport d’évaluation de résumé pour tous les objets de base de données qui ont été évaluées ou converti. Vous pouvez également afficher un rapport de synthèse pour des objets individuels :  
  
    -   Pour afficher le rapport pour une base de données, sélectionnez la base de données dans l’Explorateur de métadonnées Sybase.  
  
    -   Pour afficher le rapport pour un objet de base de données individuelle, sélectionnez l’objet dans l’Explorateur de métadonnées Sybase. Les objets qui présentent des problèmes de conversion ont une icône d’erreur rouge.  
  
Pour les objets en échec de conversion, vous pouvez afficher la syntaxe qui a entraîné l’échec de conversion.  
  
**Pour afficher les problèmes de conversion individuels**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, développez **bases de données**.  
  
2.  Développez la base de données qui affiche une icône d’erreur rouge.  
  
3.  Développez le **schémas** dossier, puis développez le schéma qui affiche une icône d’erreur rouge.  
  
4.  Sous le schéma, développez un dossier qui a une icône d’erreur rouge.  
  
5.  Sélectionnez l’objet qui a une icône d’erreur rouge.  
  
6.  Dans le volet droit, sélectionnez le **rapport** onglet.  
  
7.  En haut de la **rapport** onglet est une liste déroulante. Si la liste affiche **statistiques**, modifiez la sélection à **Source**.  
  
    SSMA affichera le code source et plusieurs boutons immédiatement au-dessus du code.  
  
8.  Sélectionnez **problème suivant**, une icône d’erreur rouge avec une flèche pointant vers la droite.  
  
    SSMA pour SAP ASE met en évidence le premier code source problématiques qu’il trouve dans l’objet actuel.  
  
Pour chaque élément qui ne peut pas être converti, vous devez déterminer ce que vous voulez faire avec cet objet :  
  
-   Vous pouvez modifier le code source des procédures et des déclencheurs sur les **SQL** onglet.  
  
-   Vous pouvez modifier l’objet SAP ASE pour supprimer ou de réviser le code problématique. Pour charger le code mis à jour dans SSMA, vous devez mettre à jour les métadonnées. Pour plus d’informations, consultez [connexion à SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure et l’Explorateur de métadonnées de Sybase, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure et la migration des données à partir de SAP ASE.  
  
## <a name="next-steps"></a>Étapes suivantes  
L’étape suivante du processus de migration est [le chargement des objets de base de données convertis dans SQL Server / SQL Azure (SybaseToSQL)](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
## <a name="see-also"></a>Voir aussi  
[Migration SAP ASE bases de données SQL Server - Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
