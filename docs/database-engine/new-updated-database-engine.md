---
title: "Mise à jour - Documentation du moteur de base de données | Microsoft Docs"
description: "Affichez des extraits de contenu mis à jour récemment dans la documentation du moteur de base de données."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: barbkess
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: database-engine
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: ce80496cdf82c2bc2df2447ed043216e6c78ad7e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-database-engine-docs"></a>Nouveau et récemment mis à jour : documentation du moteur de base de données



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **18-07-2017** &nbsp; au &nbsp; **11-09-2017**
- *Domaine :* &nbsp; **Moteur de base de données**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Installation de SQL Server](install-windows/installation-for-sql-server.md)
2. [Mises à niveau de version et d’édition prises en charge pour SQL Server 2017](install-windows/supported-version-and-edition-upgrades-2017.md)
3. [Moteur de base de données SQL Server](sql-server-database-engine-overview.md)
4. [Nouveautés du moteur de base de données - SQL Server 2016](whats-new-in-sql-server-2016.md)
5. [Nouveautés du moteur de base de données - SQL Server 2017](whats-new-in-sql-server-2017.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Amorçage automatique pour les réplicas secondaires](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-automatic-seeding-for-secondary-replicasavailability-groupswindowsautomatic-seeding-secondary-replicasmd"></a>1. &nbsp; [Amorçage automatique pour les réplicas secondaires](availability-groups/windows/automatic-seeding-secondary-replicas.md)

*Date de mise à jour : 21-08-2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 55.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0b7b6a23f38bfe5959ccd170527a9bbdb308dc4b dc51fdf69649ed6cae03584cff7bc900d5b72149  (PR=2896  ,  Filename=automatic-seeding-secondary-replicas.md  ,  Dirpath=docs\database-engine\availability-groups\windows\  ,  MergeCommitSha40=80642503480add90fc75573338760ab86139694c) -->



Dans SQL Server 2016 et antérieur, le dossier où la base de données est créée par l’amorçage automatique doit déjà exister et avoir le même chemin que sur le réplica principal.

Dans SQL Server 2017, Microsoft recommande d’utiliser les mêmes chemins de fichiers journaux et de fichiers de données sur tous les réplicas qui participent à un groupe de disponibilité, mais vous pouvez utiliser des chemins différents si nécessaire. Par exemple, dans un groupe à haute disponibilité multiplateforme, une instance de SQL Server est sur Windows et une autre instance de SQL Server est sur Linux. Les différentes plateformes ont des chemins par défaut différents. SQL Server 2017 prend en charge les réplicas de groupe de disponibilité sur les instances de SQL Server avec des chemins par défaut différents.

Le tableau suivant présente des exemples de dispositions de disques de données prises en charge qui peuvent prendre en charge l’amorçage automatique :

|Instance principale</br>Chemin de données par défaut|Instance secondaire</br>Chemin de données par défaut|Instance principale</br>Emplacement du fichier source|Instance secondaire</br> Emplacement du fichier cible
|:------|:------|:------|:------
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\ |/var/opt/mssql/data/|
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\group1\\ |/var/opt/mssql/data/group1/|
|c:\\data\\ |d:\\data\\ |c:\\data\\ |d:\\data\\
|c:\\data\\ |d:\\data\\ |c:\\data\\group1\\ |d:\\data\\group1\

Les scénarios, où l’emplacement de la base de données du réplica principal et secondaire n’est pas le chemin par défaut de l’instance, ne sont pas impactés par cette modification. Les conditions qui exigent que les chemins de fichiers de réplica secondaire correspondent aux chemins de fichiers de réplica principal restent les mêmes.

|Instance principale</br>Chemin de données par défaut|Instance secondaire</br>Chemin de données par défaut|Instance principale</br>Emplacement du fichier|Instance secondaire</br> Emplacement du fichier
|:------|:------|:------|:------
|c:\\data\\ |c:\\data\\ |d:\\group1\\ |d:\\group1\\
|c:\\data\\ |c:\\data\\ |d:\\data\\ |d:\\data\\
|c:\\data\\ |c:\\data\\ |d:\\data\\group1\\ |d:\\data\\group1\\

Si vous mélangez des chemins par défaut et non par défaut sur les réplicas principaux et secondaires, SQL Server 2017 se comporte différemment des versions précédentes. Le tableau suivant montre le comportement de SQL Server 2017.







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Domaines avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 12) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (5 + 0) : **Se connecter à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (5 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (19 + 82) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (1 + 8) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (12 + 1) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (0 + 1) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (7 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (1 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (0 + 2) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (1 + 4) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (4 + 1) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)
- [Nouveaux + Mis à jour (0 + 1) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Domaines sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


