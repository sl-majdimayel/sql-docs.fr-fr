---
title: Télécharger SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssdt
ms.topic: conceptual
keywords:
- installer ssdt, télécharger ssdt, dernière version ssdt
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 596a32bc9942bde7a8301635150287f63a5fbeed
ms.sourcegitcommit: 2111068372455b5ec147b19ca6dbf339980b267d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58431341"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Télécharger et installer SQL Server Data Tools (SSDT) pour Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


**SQL Server Data Tools** est un outil de développement moderne permettant de générer des bases de données relationnelles SQL Server, des bases de données SQL Azure, des modèles de données AS (Analysis Services), des packages IS (Integration Services) et des rapports RS (Reporting Services). Avec SSDT, vous pouvez concevoir et déployer tout type de contenu SQL Server avec la même facilité que lorsque vous développez une application dans Visual Studio.

*Pour la plupart des utilisateurs, SSDT (SQL Server Data Tools) est installé en même temps que Visual Studio. Le programme d’installation de Visual Studio installe les fonctionnalités SSDT de base. Vous devez donc exécuter le [programme d’installation autonome de SSDT](#ssdt-for-vs-2017-standalone-installer) pour bénéficier des outils AS, IS et RS*.

## <a name="install-ssdt-with-visual-studio-2017"></a>Installer SSDT avec Visual Studio 2017

Pour installer SSDT dans le cadre de [l’installation de Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), sélectionnez la charge de travail **Stockage et traitement des données**, puis **SQL Server Data Tools**. Si Visual Studio est déjà installé, vous pouvez [modifier la liste des charges de travail](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) pour inclure SSDT : ![Charge de travail Stockage et traitement des données](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)

## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installer les outils Analysis Services, Integration Services et Reporting Services

Pour installer la prise en charge des projet AS, IS et RS, exécutez le [programme d’installation autonome de SSDT](#ssdt-for-vs-2017-standalone-installer). 

Le programme d’installation répertorie les instances disponibles de Visual Studio auxquelles vous pouvez ajouter les outils SSDT. Si Visual Studio n’est pas installé, vous pouvez sélectionner **Installer une nouvelle instance de SQL Server Data Tools** pour installer SSDT avec une version minimale de Visual Studio. Toutefois, pour bénéficier d’une expérience optimale, nous vous recommandons d’utiliser SSDT avec [la dernière version de Visual Studio](https://www.visualstudio.com/downloads). 

![sélectionner AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT pour Visual Studio 2017 (programme d’installation autonome)

[![télécharger](../ssdt/media/download.png) Télécharger SSDT pour Visual Studio 2017 (15.9.0)](https://go.microsoft.com/fwlink/?linkid=2052454) 

> [!IMPORTANT]
> - Avant d’installer SSDT pour Visual Studio 2017 (15.9.0), désinstallez les extensions *Projets Analysis Services* et *Projets Reporting Services* si elles sont déjà installées, puis fermez toutes les instances de VS.
> - Utilisez SSDT pour Visual Studio 2017 (15.8.0) ou les versions antérieures pour concevoir des packages SSIS qui contiennent une source/destination Teradata. SSDT pour Visual Studio 2017 après la version 15.8.0 ne peut pas concevoir de packages SSIS qui contiennent une source/destination Teradata par Attunity.


**Informations sur la version**  
  
Numéro de version : 15.9.0  
Numéro de build : 14.0.16186.0  
Date de publication : 28 janvier 2019  

Pour obtenir une liste complète des modifications, consultez [Notes de publication pour SQL Server Data Tools (SSDT)](release-notes-ssdt.md).

SSDT pour Visual Studio 2017 nécessite la même [configuration](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) que Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Langues disponibles : SSDT pour VS 2017

Vous pouvez installer cette version de **SSDT pour VS 2017** dans les langues suivantes :

- [Chinois (simplifié)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x804)
- [Chinois (traditionnel)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x404)
- [Anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x409)
- [Français]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x40c)
- [Allemand]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x407)
- [Italien]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x410)
- [Japonais]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x411)
- [Coréen]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x412)
- [Portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x416)
- [Russe]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x419)
- [Espagnol]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x40a)

## <a name="offline-install"></a>Installation hors connexion

Pour installer SSDT lorsque vous n’êtes pas connecté à Internet, suivez les étapes de cette section. Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio).

Commencez par effectuer les étapes suivantes tant que vous êtes en ligne :

1. [Télécharger le programme d’installation autonome SSDT](#ssdt-for-vs-2017-standalone-installer).
2. [Télécharger vs_sql.exe](https://aka.ms/vs/15/release/vs_sql.exe).
3. Pendant que vous êtes toujours en ligne, exécutez l’une des commandes suivantes pour télécharger tous les fichiers nécessaires à l’installation hors connexion. L’utilisation de l’option `--layout` est primordiale. Elle permet de télécharger les fichiers en vue d’une installation hors connexion. Remplacez `<filepath>` par le vrai chemin des dispositions pour y enregistrer les fichiers.

   
   A.   Pour une langue spécifique, passez les paramètres régionaux : `vs_sql.exe --layout c:\<filepath> --lang en-us` (une seule langue correspond environ à 1 Go)  
   B. Pour toutes les langues, omettez l’argument `--lang` : `vs_sql.exe --layout c:\<filepath>` (toutes les langues correspondent environ à 3,9 Go).

4. Exécutez `SSDT-Setup-ENU.exe /layout c:\<filepath>` pour extraire la charge utile SSDT dans l’emplacement `<filepath>` où les fichiers Visual Studio 2017 ont été téléchargés. De cette façon, tous les fichiers sont réunis dans un seul dossier de dispositions.

Après avoir effectué les étapes précédentes, vous pouvez effectuer ce qui suit hors connexion :

1. Exécutez `vs_setup.exe --NoWeb` pour installer l’interpréteur de commandes de VS 2017 et le projet de données SQL Server.
2. À partir du dossier de dispositions, exécutez `SSDT-Setup-ENU.exe /install`, puis sélectionnez SSRS/SSIS/SSAS.

   - Ou pour une installation sans assistance, exécutez `SSDT-Setup-ENU.exe /INSTALLALL[:vsinstances] /passive`  

Pour les options disponibles, exécutez `SSDT-Setup-ENU.exe /help`

> [!NOTE]
> Si vous utilisez une version complète de Visual Studio 2017, créez un dossier en mode hors connexion pour SSDT uniquement et exécutez `SSDT-Setup-ENU.exe` à partir de ce dossier nouvellement créé. (N’ajoutez pas SSDT à une autre disposition hors connexion de Visual Studio 2017). Si vous ajoutez la disposition SSDT à une disposition hors connexion existante de Visual Studio, les composants d’exécution (.exe) nécessaires ne sont pas créés ici.

## <a name="supported-sql-versions"></a>Versions de SQL prises en charge
  
|Modèles de projet|Plateformes SQL prises en charge|  
|-------------------|--------------------|  
|Bases de données relationnelles|  SQL Server 2005\* - SQL Server 2017<br> (utilisez SSDT 17.x ou SSDT pour Visual Studio 2017 pour vous connecter à [SQL Server sur Linux](../linux/sql-server-linux-overview.md))<br /><br />Azure SQL Database<br /><br />Azure SQL Data Warehouse (prend uniquement en charge les requêtes ; les projets de base de données ne sont pas encore pris en charge)<br /><br /> \* La prise en charge de SQL Server 2005 est dépréciée,<br /><br /> passez à une version de SQL officiellement prise en charge|
|Modèles Analysis Services<br /><br />Reporting Services, rapports | SQL Server 2008 - SQL Server 2017|
|Integration Services, packages| SQL Server 2012 - SQL Server 2019 |
  
## <a name="dacfx"></a>DacFx

SSDT pour Visual Studio 2015 et SSDT pour Visual Studio 2017 utilisent tous les deux DacFx 17.4.1 : [Télécharger le framework d’application de la couche Données (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).

## <a name="previous-versions"></a>Versions précédentes

Pour télécharger et installer SSDT pour Visual Studio 2015 ou une version précédente de SSDT, consultez [Versions précédentes de SQL Server Data Tools (SSDT et SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md).

## <a name="next-steps"></a>Étapes suivantes

Après l’installation de SSDT, parcourez ces didacticiels pour apprendre à créer des bases de données, des packages, des modèles de données et des rapports à l’aide de SSDT :  

- [Développement de base de données hors connexion orienté projet](project-oriented-offline-database-development.md)  
- [Tutoriel SSIS : Créer un package ETL simple](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Didacticiels sur Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
- [Créer un rapport de tableau de base (didacticiel SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="see-also"></a> Voir aussi

[Forum MSDN SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog de l’équipe SSDT](https://blogs.msdn.com/b/ssdt/)  
[Référence de l’API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
