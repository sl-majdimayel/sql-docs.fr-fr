---
title: "Leçon 1 : Création d’une base de données exemple abonné | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4d862dc34dcbb81ce8d50cfac53d81a80f47d29c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---

# <a name="lesson-1-creating-a-sample-subscriber-database"></a>Leçon 1 : Création d'un exemple de base de données de l'abonné

Dans cette leçon de didacticiel [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] , vous allez créer une petite base de données d’« abonnés » pour stocker des données d’abonnement qui seront utilisées par un abonnement piloté par les données. Quand l’abonnement est traité, le serveur de rapports extrait ces données et les utilise pour personnaliser le résultat du rapport. Par exemple, les lignes de données incluent des numéros de commande spécifiques à utiliser pour les filtres, ainsi que le format de fichier des rapports générés.  
  
Cette leçon suppose que vous utilisez [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)] pour créer une base de données SQL Server.  
  
### <a name="to-create-a-sample-subscriber-database"></a>Pour créer une base de données d'abonnés exemple  
  
1.  Démarrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]et ouvrez une connexion à une instance du [!INCLUDE[ssDEnoversion_md](../includes/ssdenoversion-md.md)].  
  
2.  Cliquez avec le bouton droit sur Bases de données, puis sélectionnez **Nouvelle base de données**.  
  
3.  Dans la boîte de dialogue Nouvelle base de données, dans la zone **Nom de la base de données**, tapez *Abonnés*. 
4. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Cliquez sur le bouton **Nouvelle requête** dans la barre d’outils.  
  
6.  Copiez les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] suivantes dans la requête vide :  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
7.  Cliquez sur  **Exécutez** sur la barre d’outils.  
  
8.  Utilisez une instruction SELECT pour vérifier que votre table comporte bien trois lignes de données. Par exemple : `select * from OrderInfo`  
  
## <a name="next-steps"></a>Étapes suivantes  
+ Vous avez créé les données d'abonnement sur lesquelles seront basées la distribution des rapports et en fonction desquelles les résultats des rapports varieront pour chaque abonné. 
+ Ensuite, vous allez modifier les propriétés de la source de données du rapport pour utiliser des informations d’identification stockées. 
+ Vous allez également modifier la conception du rapport afin d'inclure un paramètre que l'abonnement utilisera avec les données d'abonné. [Leçon 2 : Modification des propriétés d’une source de données de rapport](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)  

## <a name="next-steps"></a>Étapes suivantes

[Créer un abonnement piloté par les données](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)  
[Créer une base de données](../relational-databases/databases/create-a-database.md)  
[Créer un rapport de tableau de base](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)