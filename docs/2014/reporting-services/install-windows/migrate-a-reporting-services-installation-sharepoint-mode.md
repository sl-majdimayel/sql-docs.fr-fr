---
title: Migrer une installation Reporting Services (mode SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 61290949-690a-4e19-b078-57c99b6b30fa
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: fb3d7e60db2e5827c61ff2c80dbaf674262621f7
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030240"
---
# <a name="migrate-a-reporting-services-installation-sharepoint-mode"></a>Migrer une installation Reporting Services (mode SharePoint)
  Cette rubrique est une vue d'ensemble des étapes nécessaires pour migrer un déploiement en mode de SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] d'un environnement SharePoint vers un autre. Les étapes spécifiques peuvent être différentes selon la version à partir de laquelle vous migrez. Pour plus d'informations sur les scénarios de mise à niveau et de migration pour le mode SharePoint, consultez [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md). Si vous voulez uniquement copier les éléments de rapport à partir d’un serveur vers un autre, consultez [Exemple de script Reporting Services rs.exe pour migrer le contenu entre des serveurs de rapports](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Pour plus d’informations sur la migration d’un déploiement en mode natif de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez [Faire migrer une installation Reporting Services &#40;mode natif&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 et SharePoint 2013|  
  
 La principale raison pour laquelle vous effectuez une migration est lorsque vous voulez mettre à niveau votre déploiement de SharePoint 2010 vers SharePoint 2013. SharePoint 2013 ne prend pas en charge la mise à niveau sur place de SharePoint 2010 et vous devez exécuter la procédure de **mise à niveau avec liaison des bases de données** ou de migration de contenu uniquement.  
  
 Pour plus d'informations sur la mise à niveau de SharePoint 2013, consultez les rubriques suivantes :  
  
-   [Présentation de la procédure de mise à niveau vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Mettre à niveau les bases de données de SharePoint 2010 vers SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
-   [Déplacer des bases de données de contenu dans SharePoint 2013](https://technet.microsoft.com/library/cc262792.aspx).  
  
 
  
##  <a name="bkmk_prior_versions"></a> Migrer à partir de versions de Reporting Services en mode SharePoint antérieures à SQL Server 2012  
 L'architecture en mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a été modifiée dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], y compris le schéma de base de données d'application de service. Si vous souhaitez migrer vers le mode SharePoint de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] une version antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], commencez par créer le nouvel environnement SharePoint en installant SharePoint et le mode SharePoint de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez [Installation Reporting Services SharePoint Mode &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
 Une fois le nouvel environnement SharePoint en cours d'exécution, choisissez une migration de contenu uniquement ou une migration complète au niveau de la base de données qui contient des bases de données de contenu.  
  
###  <a name="bkmk_content_only_migration"></a> Migration du contenu uniquement  
 **Migration du contenu de Reporting Services uniquement :** si vous devez copier le contenu [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans une nouvelle batterie, vous devez utiliser des outils comme **rs.exe** pour copier le contenu vers la nouvelle installation de SharePoint. Pour plus d'informations sur les migrations de contenu uniquement, consultez les rubriques suivantes :  
  
-   **Scripts RSS [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :** les scripts peuvent migrer le contenu et les ressources entre les serveurs de rapports en mode natif et en mode SharePoint. Pour plus d’informations, consultez [Exemple de script Reporting Services rs.exe pour migrer le contenu entre des serveurs de rapports](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md) et [script RS.exe de Reporting Services qui migre le contenu à partir d’un serveur de rapports vers un autre](http://azuresql.codeplex.com/releases/view/115207).  
  
-   **Outil de migration Reporting Services :** l'outil peut copier vos éléments de rapport d'un serveur en mode natif vers un serveur en mode SharePoint. Pour plus d'informations, consultez [Outil de migration Reporting Services](https://www.microsoft.com/download/details.aspx?id=29560).  
  
###  <a name="bkmk_full_migration"></a> Migration complète  
 **Migration complète :** si vous migrez les bases de données de contenu SharePoint avec les bases de données du catalogue de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers une nouvelle batterie, vous pouvez suivre la série d'options de sauvegarde et de restauration résumées dans cette rubrique. Dans certains cas, vous devez utiliser un autre outil pour la phase de restauration que celui utilisé pour la phase de sauvegarde. Par exemple, vous pouvez utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour sauvegarder les clés de chiffrement à partir d'une version antérieure de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , mais vous devez utiliser l'Administration centrale de SharePoint ou PowerShell pour restaurer les clés de chiffrement dans une installation en mode SharePoint de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
####  <a name="bkmk_databases"></a> Bases de données que vous voyez dans la migration terminée  
 Le tableau suivant décrit les bases de données SQL Server liées à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dont vous disposerez après avoir migré avec succès votre installation SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
|Base de données|Exemple de nom||  
|--------------|------------------|-|  
|Base de données de catalogue|ReportingService_[GUID application service] **(\*)**|L'utilisateur migre.|  
|Base de données temporaire|ReportingService_[service application GUID]TempDB **(\*)**|L'utilisateur migre.|  
|Base de données d'alertes|ReportingService_[GUID application service]_Alerting|Créée lorsqu'une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est créée.|  
  
 **(\*)** Les exemples de noms indiqués dans le tableau respectent les conventions d’affectation de noms que SSRS utilise lors de la création d’une application de service SSRS. Si vous migrez depuis un autre serveur, vos bases de données de catalogue et TempDB conservent les noms de l'installation d'origine.  
  
####  <a name="bkmk_backup_operations"></a> Opérations de sauvegarde  
 Cette section décrit les types d'informations que vous devez migrer et les outils ou processus utilisés pour effectuer la sauvegarde.  
  
 ![Schéma de base de la migration SSRS SharePoint](../../../2014/sql-server/install/media/rs-sharepoint-migration.gif "Schéma de base de la migration SSRS SharePoint")  
  
||Objets|Méthode|Remarques|  
|-|-------------|------------|-----------|  
|**1**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|**Rskeymgmt.exe** ou Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Consultez [Sauvegarder et restaurer les clés de chiffrement Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).|Les outils indiqués peuvent être utilisés pour la sauvegarde, mais pour l'opération de restauration vous devez utiliser les pages de gestion de l'application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou PowerShell.|  
|**2**|Bases de données de contenu SharePoint.||Sauvegardez la base de données et détachez-la.<br /><br /> Consultez la section « Mise à niveau avec liaison de base de données » de l’article [Déterminer l’approche de mise à niveau (SharePoint Server 2010) (https://technet.microsoft.com/library/cc263447.aspx)](https://technet.microsoft.com/library/cc263447.aspx).|  
|**3**|Base de données SQL Server, qui joue le rôle de base de données du catalogue de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Sauvegarde et restauration de la base de données SQL Server<br /><br /> ou Gestionnaire de configuration<br /><br /> Liez et détachez une base de données SQL Server.||  
|**4**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Simple copie du fichier.|Vous devez seulement copier rsreportserver.config si vous avez personnalisé le fichier. Exemple de l'emplacement par défaut des fichiers : C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting<br /><br /> Rsreportserver.config<br /><br /> Rssvrpolicy.config<br /><br /> Web.config pour l'application ASP.NET de serveur de rapports.<br /><br /> Machine.config pour ASP.NET.|  
  
####  <a name="bkmk_restore_operations"></a> Opérations de restauration  
 Cette section décrit les types d'informations que vous devez migrer et les outils ou processus utilisés pour effectuer la restauration. Les outils que vous utilisez pour la restauration peuvent être différents des outils vous avez utilisés pour la sauvegarde.  
  
 Avant de suivre les étapes de restauration, vous devez installer et configurer la nouvelle batterie de serveurs SharePoint et le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations sur une installation basique de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mode SharePoint, consultez [Installation Reporting Services SharePoint Mode &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
||Objets|Méthode|Remarques|  
|-|-------------|------------|-----------|  
|**1**|Restaurez les bases de données de contenu SharePoint sur la nouvelle batterie.|Méthode « Mise à niveau avec liaison de base de données » SharePoint.|Étapes de base :<br /><br /> 1) Restaurez la base de données sur le nouveau serveur.<br /><br /> 2) Attachez la base de données de contenu à une application web en indiquant l’URL.<br /><br /> 3) La commande Get-SPWebapplication répertorie toutes les applications web et les URL.<br /><br /> Consultez la section « Mise à niveau avec liaison de base de données » dans [Déterminer l’approche de mise à niveau (SharePoint Server 2010) (https://technet.microsoft.com/library/cc263447.aspx)](https://technet.microsoft.com/library/cc263447.aspx)et [Attacher des bases de données et mettre à niveau avec SharePoint Server 2010 (https://technet.microsoft.com/library/cc263299.aspx)](https://technet.microsoft.com/library/cc263299.aspx).|  
|**2**|Restaurez la base de données SQL qui joue le rôle de base de données de catalogue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (ReportServer).|Sauvegardez et restaurez les bases de données SQL.<br /><br /> **ou Gestionnaire de configuration**<br /><br /> Liez et détachez la base de données SQL Server.|Lors de la première utilisation de la base de données, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] met à jour le schéma de la base de données selon les besoins pour qu'elle fonctionne avec l'environnement [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**3**|Créez une nouvelle application de service de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Administration centrale de SharePoint.|Lorsque vous créez une application de service, configurez-la pour utiliser la base de données du serveur de rapports que vous avez copiée.<br /><br /> Pour plus d’informations sur l’utilisation de l’Administration centrale de SharePoint, consultez la section « Étape 3 : Section créer une Application de Service Reporting Services » dans [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).<br /><br /> Pour voir des exemples d’utilisation de PowerShell, consultez la section « Pour créer une application de service Reporting Services à l’aide de PowerShell » dans [Service et applications de service Reporting Services SharePoint](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).|  
|**4**|Restaurez les fichiers de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Simple copie du fichier.|Exemple de l'emplacement par défaut des fichiers : C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting|  
|**5**|Restaurez les clés de chiffrement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Restaurez le fichier de sauvegarde des clés via la page « SystemSettings » de l’application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> **ou Gestionnaire de configuration**<br /><br /> PowerShell.|Consultez la section « Gestion des clés » de la rubrique [Gérer une application de service Reporting Services SharePoint](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).|  
  
#####  <a name="bkmk_additional_configuration"></a> Configuration supplémentaire  
 En fonction de la configuration de votre environnement SharePoint précédent, vous devrez peut-être effectuer une ou plusieurs des opérations suivantes :  
  
1.  Configurez l'authentification NTLM pour une application de service de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour plus d’informations, consultez [Configurer la messagerie électronique pour une application de service Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  
##  <a name="bkmk_migrate_from_ctp"></a> Migrer à partir d’un déploiement de SQL Server 2012  
 Dans une batterie à plusieurs serveurs, les utilisateurs auront probablement placer les bases de données de contenu et de catalogue sur des ordinateurs différents, auquel cas vous devez simplement ajouter un nouveau serveur avec le service de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé, à la batterie de serveurs SharePoint, puis supprimer l'ancien serveur. Vous ne devriez pas avoir besoin de copier de bases de données.  
  
### <a name="backup-operations"></a>Opérations de sauvegarde  
  
1.  Sauvegardez les clés de chiffrement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Sauvegardez de l'application de service de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans l'Administration centrale de SharePoint (ou avec PowerShell). Cette opération sauvegarde également les bases de données de l'application de service dans SharePoint. Consultez la rubrique  [Sauvegarder et restaurer des applications de service SharePoint Reporting Services](../../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md).  
  
3.  Si vous avez un compte d'exécution sans assistance (UEA) et que vous utilisez l'authentification Windows, prenez note des informations d'identification pour que vous puissiez les utiliser pour le processus de restauration.  
  
4.  Pour plus d'informations, consultez [Sauvegarder les applications de service dans SharePoint 2013](https://technet.microsoft.com/library/ee428318.aspx).  
  
### <a name="restore-operations"></a>Opérations de restauration  
  
1.  Restaurez l'application de service de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à l'aide de l'Administration centrale de SharePoint. Vous pouvez également utiliser PowerShell.  
  
2.  Restaurez les clés de chiffrement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     Consultez la section « Gestion des clés » de la rubrique [Gérer une application de service Reporting Services SharePoint](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
3.  Configurez le compte UEA et les informations d'identification Windows dans l'application de service.  
  
4.  Pour plus d'informations, consultez [Restaurer les applications de service dans SharePoint 2013](https://technet.microsoft.com/library/ee428305.aspx).  
  
##  <a name="bkmk_additional_resources"></a> Ressources supplémentaires  
  
-   [Prendre en main les mises à niveau vers SharePoint 2013 (https://technet.microsoft.com/library/ee833948.aspx)](https://technet.microsoft.com/library/ee833948.aspx).  
  
-   [Présentation de la procédure de mise à niveau vers SharePoint 2013 (https://technet.microsoft.com/library/cc262483.aspx)](https://technet.microsoft.com/library/cc262483.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 [Faire migrer une installation Reporting Services &#40;mode natif&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
  
