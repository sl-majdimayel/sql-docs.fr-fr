---
title: Événements étendus pour la surveillance des processus R et Python - SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 96b791d98aa7fee588e4f72b76a733f48917f77a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513116"
---
# <a name="extended-events-for-sql-server-machine-learning-services"></a>Événements étendus pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server fournit un ensemble d’événements étendus pour résoudre les opérations liées à la [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], ainsi que les travaux de Python ou R envoyés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

**S’applique à :**  SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

## <a name="sql-server-events-for-machine-learning"></a>Événements de SQL Server pour l’apprentissage

Pour afficher une liste des événements liés à SQL Server, exécutez la requête suivante à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

```sql
SELECT o.name AS event_name, o.description
FROM sys.dm_xe_objects o
JOIN sys.dm_xe_packages p
ON o.package_guid = p.guid
WHERE o.object_type = 'event'
AND p.name = 'SQLSatellite';
```

Pour obtenir des informations générales sur l’utilisation des événements étendus, consultez [outils événements étendus](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).

> [!TIP]
> Pour les événements étendus générés par SQL Server, essayez la nouvelle [SSMS XEvent profiler](https://docs.microsoft.com/sql/relational-databases/extended-events/use-the-ssms-xe-profiler). Cette nouvelle fonctionnalité dans Management Studio affiche une visualisation en direct pour les événements étendus et est moins importun à SQL Server qu’une trace de Profiler similaire.

## <a name="additional-events-specific-to-machine-learning-components"></a>Événements supplémentaires spécifiques aux composants d’apprentissage automatique

Événements étendus supplémentaires sont disponibles pour les composants qui sont liés aux et utilisées par SQL Server Machine Learning Services, tels que le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]et BXLServer, le processus satellite qui démarre le runtime R. Ces événements étendus supplémentaires sont déclenchés dans les processus externes et doivent donc être capturées à l’aide d’un utilitaire externe.

Pour plus d’informations sur la procédure à suivre, consultez la section [collecte d’événements à partir de processus externes](#bkmk_externalevents).

##  <a name="bkmk_xeventtable"></a> Tableau des événements étendus

|Événement|Description|Remarques|  
|-----------|-----------------|---------|  
|connection_accept|Se produit lorsqu’une nouvelle connexion est acceptée. Cet événement permet de journaliser toutes les tentatives de connexion.||  
|failed_launching|Le lancement a échoué.|Indique une erreur.|  
|satellite_abort_connection|Enregistrement d’abandon de connexion||  
|satellite_abort_received|Se déclenche lorsqu’un message d’abandon est reçu sur une connexion satellite.||  
|satellite_abort_sent|Se déclenche lorsqu’un message d’abandon est envoyé sur une connexion satellite.||  
|satellite_authentication_completion|Se déclenche lorsque l'authentification est terminée pour une connexion sur TCP ou Namedpipe.||  
|satellite_authorization_completion|Se déclenche lorsque l'autorisation est effectuée pour une connexion sur TCP ou Namedpipe.||  
|satellite_cleanup|Se déclenche lorsque le satellite appelle la fonction de nettoyage.|Déclenché uniquement à partir de processus externes. Consultez les instructions sur la collecte d'événements à partir de processus externes.|  
|satellite_data_chunk_sent|Se déclenche lorsque la connexion satellite termine l'envoi d'un bloc de données unique.|L’événement indique le nombre de lignes envoyées, le nombre de colonnes, le nombre de paquets SNI utilisés et le temps écoulé en millisecondes pendant l’envoi du bloc. Ces informations peuvent vous aider à comprendre le temps nécessaire à la transmission des différents types de données, ainsi que le nombre de paquets utilisés.|  
|satellite_data_receive_completion|Se déclenche lorsque toutes les données requises par une requête sont reçues sur la connexion satellite.|Déclenché uniquement à partir de processus externes. Consultez les instructions sur la collecte d'événements à partir de processus externes.|  
|satellite_data_send_completion|Se déclenche lorsque toutes les données requises pour une session sont envoyées sur la connexion satellite.||  
|satellite_data_send_start|Se déclenche lors de la transmission de données démarre.| Transmission de données démarre juste avant que le premier segment de données est envoyé.|  
|satellite_error|Utilisé pour le traçage des erreurs de satellite sql||  
|satellite_invalid_sized_message|La taille du message n’est pas valide||  
|satellite_message_coalesced|Utilisé pour fusionner les messages de traçage sur la couche réseau||  
|satellite_message_ring_buffer_record|Enregistrement de la mémoire tampon en anneau du message||  
|satellite_message_summary|Informations récapitulatives de la messagerie||  
|satellite_message_version_mismatch|Le champ de version du message ne correspond pas||  
|satellite_messaging|Utilisé pour le traçage des événements de messagerie (lier, dissocier etc.)||  
|satellite_partial_message|Utilisé pour le traçage des messages partiels sur la couche réseau||  
|satellite_schema_received|Se déclenche lorsque le message de schéma est reçu et lu par SQL.||  
|satellite_schema_sent|Se déclenche lorsque le message de schéma est envoyé par le satellite.|Déclenché uniquement à partir de processus externes. Consultez les instructions sur la collecte d'événements à partir de processus externes.|  
|satellite_service_start_posted|Se déclenche lorsque le message de démarrage de service est envoyé à Launchpad.|Ce message indique à Launchpad de démarrer le processus externe, et contient un ID pour la nouvelle session.|  
|satellite_unexpected_message_received|Se déclenche lors de la réception d'un message inattendu.|Indique une erreur.|  
|stack_trace|Se produit lors d'une demande de vidage mémoire pour le processus.|Indique une erreur.|  
|trace_event|Utilisé à des fins de traçage|Ces événements peuvent contenir des messages de trace de SQL Server, de Launchpad et de processus externes. Cela comprend la sortie vers stdout et stderr à partir de R.|  
|launchpad_launch_start|Se déclenche lorsque Launchpad démarre le lancement d’un satellite.|Déclenché uniquement à partir de Launchpad. Consultez les instructions sur la collecte d'événements à partir de launchpad.exe.|  
|launchpad_resume_sent|Se déclenche lorsque launchpad a lancé le satellite et envoyé un message de reprise à SQL Server.|Déclenché uniquement à partir de Launchpad. Consultez les instructions sur la collecte d'événements à partir de launchpad.exe.|  
|satellite_data_chunk_sent|Se déclenche lorsque la connexion satellite termine l'envoi d'un bloc de données unique.|Contient des informations sur le nombre de colonnes, le nombre de lignes, le nombre de paquets et le temps écoulé pour l’envoi du bloc.|  
|satellite_sessionId_mismatch|L’ID de session du message n’était pas attendu||  
  
###  <a name="bkmk_externalevents"></a> Collecte des événements à partir de processus externes

SQL Server Machine Learning Services lance des services qui s’exécutent en dehors du processus SQL Server. Pour capturer les événements liés à ces processus externes, vous devez créer un fichier de configuration de trace les événements et placez le fichier dans le même répertoire que l’exécutable du processus.  
  
+ **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
    Pour capturer les événements liés à Launchpad, placez le fichier *.config* dans le répertoire Binn de l’instance SQL Server.  Dans une installation par défaut, il s’agit de la configuration :

    `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn` .  
  
+ **BXLServer** est le processus satellite qui prend en charge d’extensibilité SQL avec des langages de script externes, tels que R ou Python. Une instance distincte de BxlServer est démarrée pour chaque instance de langage externe.
  
    Pour capturer les événements liés à BXLServer, placez le *.config* fichier dans le répertoire d’installation de R ou Python.  Dans une installation par défaut, il s’agit de la configuration :
     
    **R:** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  

    **Python :** `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\PYTHON_SERVICES\library\RevoScaleR\rxLibs\x64`.

Le fichier de configuration doit porter le même que le fichier exécutable, en utilisant le format « [nom].xevents.Xml ». En d'autres termes, les fichiers doivent être nommés comme suit :

+ `Launchpad.xevents.xml`
+ `bxlserver.xevents.xml`

Le fichier de configuration lui-même a le format suivant :

```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="[session name]" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="you">Xevent for launchpad or bxl server.</description>  
    <event package="SQLSatellite" name="[XEvent Name 1]" />  
    <event package="SQLSatellite" name="[XEvent Name 2]" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="[SessionName].xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ Pour configurer la trace, modifiez le *nom de la session* espace réservé, l’espace réservé pour le nom de fichier (`[SessionName].xel`) et les noms des événements que vous souhaitez capturer, par exemple, `[XEvent Name 1]`, `[XEvent Name 1]`).  
+ N’importe quel nombre de balises de package d’événement peut sembler et est collecté tant que l’attribut de nom est correct.

### <a name="example-capturing-launchpad-events"></a>Exemple : Capture d’événements de Launchpad

L’exemple suivant montre la définition d’une trace d’événements pour le service Launchpad :

```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="launchpad_launch_start" />  
    <event package="SQLSatellite" name="launchpad_resume_sent" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="launchpad_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ Placez le fichier *.config* dans le répertoire Binn de l’instance SQL Server.
+ Ce fichier doit être nommé `Launchpad.xevents.xml`.

### <a name="example-capturing-bxlserver-events"></a>Exemple : Capture des événements de BXLServer  

L'exemple suivant montre la définition d'une trace d'événements pour le service BXLServer.
  
```xml
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
 <event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="satellite_abort_received" />  
    <event package="SQLSatellite" name="satellite_authentication_completion" />  
    <event package="SQLSatellite" name="satellite_cleanup" />  
    <event package="SQLSatellite" name="satellite_data_receive_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_start" />  
    <event package="SQLSatellite" name="satellite_schema_sent" />   
    <event package="SQLSatellite" name="satellite_unexpected_message_received" />    
    <event package="SQLSatellite" name="satellite_data_chunk_sent" />   
    <target package="package0" name="event_file">  
      <parameter name="filename" value="satellite_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
```

+ Placez le fichier *.config* dans le même répertoire que l’exécutable BXLServer.
+ Ce fichier doit être nommé `bxlserver.xevents.xml`.

## <a name="see-also"></a>Voir aussi

[Rapports personnalisés Management Studio pour Machine Learning Services](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)
