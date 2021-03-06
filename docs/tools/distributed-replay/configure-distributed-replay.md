---
title: Configurer Distributed Replay | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: aee11dde-daad-439b-b594-9f4aeac94335
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 166e5e929863a9c7213f3cda6f43e6c1007865b2
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125559"
---
# <a name="configure-distributed-replay"></a>Configure Distributed Replay
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les détails de configuration de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Utility sont spécifiés dans les fichiers XML qui se trouvent sur Distributed Replay Controller, sur les clients et à l'emplacement où l'outil d'administration est installé. Il s'agit des fichiers suivants :  
  
-   [Fichier de configuration du contrôleur](#DReplayController)  
  
-   [Fichier de configuration du client](#DReplayClient)  
  
-   [Fichier de configuration de prétraitement](#PreprocessConfig)  
  
-   [Fichier de configuration de relecture](#ReplayConfig)  
  
##  <a name="DReplayController"></a> Fichier de configuration du contrôleur : DReplayController.config  
 Lorsque le service Distributed Replay Controller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre, il charge le niveau de journalisation à partir du fichier de configuration du contrôleur, `DReplayController.config`. Ce fichier se trouve dans le dossier où vous avez installé le service Distributed Replay Controller :  
  
 **\<chemin d’installation du contrôleur>\DReplayController.config**  
  
 Le niveau de journalisation spécifié par le fichier de configuration du contrôleur inclut les éléments suivants :  
  
|Paramètre|Élément XML|Description|Valeurs autorisées|Requis|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Niveau de journalisation|`<LoggingLevel>`|Spécifie le niveau de journalisation pour le service contrôleur.|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|Non. Par défaut, la valeur est `CRITICAL`.|  
  
### <a name="example"></a> Exemple  
 Cet exemple montre un fichier de configuration du contrôleur qui a été modifié pour supprimer les entrées du journal `INFORMATION` et `WARNING` .  
  
```  
<?xml version='1.0'?>  
<Options>  
<LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="DReplayClient"></a> Fichier de configuration du client : DReplayClient.config  
 Lorsque le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client démarre, il charge des paramètres de configuration à partir du fichier de configuration client, `DReplayClient.config`. Ce fichier se trouve sur chaque client, dans le dossier où vous avez installé le service Distributed Replay Client :  
  
 **\<chemin d’installation du client>\DReplayClient.config**  
  
 Les paramètres spécifiés par le fichier de configuration client incluent les éléments suivants :  
  
|Paramètre|Élément XML|Description|Valeurs autorisées|Requis|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Contrôleur|`<Controller>`|Spécifie le nom de l'ordinateur du contrôleur. Le client tentera de s'inscrire auprès de l'environnement Distributed Replay en contactant le contrôleur.|Vous pouvez utiliser «`localhost`» ou «`.`» pour désigner l'ordinateur local.|Non. Par défaut, le client tente de s'inscrire auprès de l'instance du contrôleur qui s'exécute localement («`.`»), s'il existe.|  
|Répertoire de travail du client|`<WorkingDirectory>`|Correspond au chemin d'accès local sur le client où les fichiers de distribution sont enregistrés.<br /><br /> Les fichiers de ce répertoire sont écrasés lors de la prochaine relecture.|Nom du répertoire complet, en commençant par une lettre de lecteur.|Non. Si aucune valeur n'est spécifiée, les fichiers de distribution seront enregistrés dans le même emplacement que le fichier de configuration client par défaut. Si une valeur est spécifiée et que ce dossier n'existe pas sur le client, le service client ne démarrera pas.|  
|Répertoire des résultats du client|`<ResultDirectory>`|Correspond au chemin d'accès local sur le client où est enregistré le fichier de trace de résultats de l'activité de relecture (pour le client).<br /><br /> Les fichiers de ce répertoire sont écrasés lors de la prochaine relecture.|Nom du répertoire complet, en commençant par une lettre de lecteur.|Non. Si aucune valeur n'est spécifiée, le fichier de trace de résultats sera enregistré dans le même emplacement que le fichier de configuration client par défaut. Si une valeur est spécifiée et que ce dossier n'existe pas sur le client, le service client ne démarrera pas.|  
|Niveau de journalisation|`<LoggingLevel>`|Correspond au niveau de journalisation pour le service client.|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|Non. Par défaut, la valeur est `CRITICAL`.|  
  
### <a name="example"></a> Exemple  
 Cet exemple montre un fichier de configuration client qui a été modifié pour spécifier que le service contrôleur s'exécute sur un autre ordinateur, un ordinateur nommé `Controller1`. Les éléments `WorkingDirectory` et `ResultDirectory` ont été configurés pour utiliser les dossiers `c:\ClientWorkingDir` et `c:\ResultTraceDir`, respectivement. La valeur par défaut du niveau de journalisation a été modifiée pour supprimer les entrées du journal `INFORMATION` et `WARNING` .  
  
```  
<?xml version='1.0'?>  
<Options>  
    <Controller>Controller1</Controller>  
    <WorkingDirectory>c:\ClientWorkingDir</WorkingDirectory>  
    <ResultDirectory>c:\ResultTraceDir</ResultDirectory>  
    <LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="PreprocessConfig"></a> Fichier de configuration de prétraitement : DReplay.exe.preprocess.config  
 Lorsque vous utilisez l'outil d'administration pour initialiser l'étape de prétraitement, l'outil d'administration charge les paramètres de prétraitement à partir du fichier de configuration de prétraitement, `DReplay.exe.preprocess.config`.  
  
 Utilisez le fichier de configuration par défaut ou le paramètre **-c** de l’outil d’administration pour spécifier l’emplacement d’un fichier de configuration de prétraitement modifié. Pour plus d’informations sur l’utilisation de l’option de prétraitement de l’outil d’administration, consultez [Option preprocess &#40;outil d’administration Distributed Replay&#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md).  
  
 Le fichier de configuration de prétraitement par défaut se trouve dans le dossier où vous avez installé l'outil d'administration :  
  
 **\<chemin d’installation de l’outil d’administration>\DReplayAdmin\DReplay.exe.preprocess.config**  
  
 Les paramètres de configuration de prétraitement sont spécifiés dans les éléments XML qui sont enfants de l'élément `<PreprocessModifiers>` dans le fichier de configuration de prétraitement. Ces paramètres sont les suivants :  
  
|Paramètre|Élément XML|Description|Valeurs autorisées|Requis|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Inclure les activités de session système|`<IncSystemSession>`|Indique si les activités de session système lors de la capture seront incluses lors de la relecture.|`Yes` &#124; `No`|Non. Par défaut, la valeur est `No`.|  
|Durée d'inactivité maximale|`<MaxIdleTime>`|Limite la durée d'inactivité à un nombre absolu (en secondes).|Entier qui est >= -1.<br /><br /> `-1` n'indique aucune modification de la valeur d'origine dans le fichier de trace d'origine.<br /><br /> `0` indique qu'une activité continue à un instant donné dans le temps.|Non. Par défaut, la valeur est `-1`.|  
  
### <a name="example"></a> Exemple  
 Fichier de configuration de prétraitement par défaut :  
  
```  
<?xml version='1.0'?>  
<Options>  
    <PreprocessModifiers>  
        <IncSystemSession>No</IncSystemSession>  
        <MaxIdleTime>-1</MaxIdleTime>  
    </PreprocessModifiers>  
</Options>  
```  
  
##  <a name="ReplayConfig"></a> Fichier de configuration de relecture : DReplay.exe.replay.config  
 Lorsque vous utilisez l'outil d'administration pour initialiser l'étape de relecture d'événement, l'outil d'administration charge les paramètres de relecture à partir du fichier de configuration de relecture, `DReplay.exe.replay.config`.  
  
 Utilisez le fichier de configuration par défaut ou le paramètre **-c** de l’outil d’administration pour spécifier l’emplacement d’un fichier de configuration de relecture modifié. Pour plus d’informations sur l’utilisation de l’option de relecture de l’outil d’administration, consultez [Option Replay &#40;outil d’administration Distributed Replay&#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md).  
  
 Le fichier de configuration de relecture par défaut se trouve dans le dossier où vous avez installé l'outil d'administration :  
  
 **\<chemin d’installation de l’outil d’administration>\DReplayAdmin\DReplay.exe.replay.config**  
  
 Les paramètres de configuration de la relecture sont spécifiés dans les éléments XML qui sont enfants des éléments `<ReplayOptions>` et `<OutputOptions>` du fichier de configuration de relecture.  
  
### <a name="replayoptions-element"></a>\<ReplayOptions > élément  
 Les paramètres spécifiés par le fichier de configuration de relecture dans l'élément `<ReplayOptions>` incluent les éléments suivants :  
  
|Paramètre|Élément XML|Description|Valeurs autorisées|Requis|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (serveur de test)|`<Server>`|Spécifie le nom du serveur et de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auxquels la connexion doit être établie.|*nom_serveur*[\\*nom_instance*]<br /><br /> Vous ne pouvez pas utiliser «`localhost`» ou «`.`» pour représenter l'hôte local.|Non, si le nom du serveur est déjà spécifié à l’aide du paramètre **-s**_serveur cible_ avec l’option **replay** de l’outil d’administration.|  
|Mode de séquencement|`<SequencingMode>`|Spécifie le mode utilisé pour la planification d'événement.|`synchronization` &#124; `stress`|Non. Par défaut, la valeur est `stress`.|  
|Granularité de l'échelle du mode simultané (stress)|`<StressScaleGranularity>`|Indique si toutes les connexions sur l'ID du profil de service (SPID) doivent être mises à l'échelle ensemble (SPID) ou indépendamment (connexion) en mode simultané (stress).|SPID &#124; Connexion|Oui. Par défaut, la valeur est `SPID`.|  
|Échelle de délai de connexion|`<ConnectTimeScale>`|Utilisée pour mettre à l'échelle le délai de connexion en mode simultané (stress).|Entier compris entre `1` et `100`.|Non. Par défaut, la valeur est `100`.|  
|Échelle de temps de réflexion|`<ThinkTimeScale>`|Est utilisé pour mettre à l'échelle le temps de réflexion en mode simultané (stress).|Entier compris entre `0` et `100`.|Non. Par défaut, la valeur est `100`.|  
|Utiliser le regroupement de connexions|`<UseConnectionPooling>`|Spécifie si le regroupement de connexions est activé sur chaque client Distributed Replay.|Oui &#124; Non|Oui. Par défaut, la valeur est `Yes`.|  
|Délai du moniteur d'intégrité|`<HealthmonInterval>`|Indique à quelle fréquence exécuter le moniteur d'intégrité (en secondes).<br /><br /> Cette valeur est utilisée uniquement en mode de synchronisation.|Entier >= 1<br /><br /> (`-1` pour désactiver)|Non. Par défaut, la valeur est `60`.|  
|Délai de requête|`<QueryTimeout>`|Spécifie la valeur du délai de requête, en secondes. Cette valeur n'est effective que jusqu'à ce que la première ligne soit retournée.|Entier >= 1<br /><br /> (`-1` pour désactiver)|Non. Par défaut, la valeur est `3600`.|  
|Threads par client|`<ThreadsPerClient>`|Spécifie le nombre de threads de relecture à utiliser pour chaque client de relecture.|Entier compris entre `1` et `512`.|Non. Si non spécifié, Distributed Replay utilise une valeur de `255`.|  
  
### <a name="outputoptions-element"></a>\<OutputOptions > élément  
 Les paramètres spécifiés par le fichier de configuration de relecture dans l'élément `<OutputOptions>` incluent les éléments suivants :  
  
|Paramètre|Élément XML|Description|Valeurs autorisées|Requis|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Nombre de lignes d'enregistrement|`<RecordRowCount>`|Indique si le nombre de lignes doit être enregistré pour chaque jeu de résultats.|`Yes` &#124; `No`|Non. Par défaut, la valeur est `Yes`.|  
|Jeu de résultats d'enregistrement|`<RecordResultSet>`|Indique si le contenu de tous les jeux de résultats doit être enregistré.|`Yes` &#124; `No`|Non. Par défaut, la valeur est `No`.|  
  
### <a name="example"></a> Exemple  
 Fichier de configuration de relecture par défaut :  
  
```  
<?xml version='1.0'?>  
<Options>  
    <ReplayOptions>  
        <Server></Server>  
        <SequencingMode>stress</SequencingMode>  
        <ConnectTimeScale></ConnectTimeScale>  
        <ThinkTimeScale></ThinkTimeScale>  
        <HealthmonInterval>60</HealthmonInterval>  
        <QueryTimeout>3600</QueryTimeout>  
        <ThreadsPerClient></ThreadsPerClient>  
    </ReplayOptions>  
    <OutputOptions>  
        <ResultTrace>  
            <RecordRowCount>Yes</RecordRowCount>  
            <RecordResultSet>No</RecordResultSet>  
        </ResultTrace>  
    </OutputOptions>  
</Options>  
```  

### <a name="possible-issue-when-running-with-synchronization-sequencing-mode"></a>Problème possible lors de l’exécution avec la synchronisation en Mode de séquencement
 Vous pouvez rencontrer un problème dans lequel la fonctionnalité de relecture semble se « blocage », ou les événements de relectures très lentement. Ce phénomène peut se produire si la cours de relecture de trace s’appuie sur les données et/ou les événements qui n’existent pas dans la base de données restaurée. 
 
 Par exemple, une charge de travail capturée utilise WAITFOR, comme dans l’instruction WAITFOR de réception de Service service Broker. Lorsque vous utilisez le mode de séquencement de synchronisation, les lots sont relus en série. Si une instruction INSERT portant sur la base de données source après la sauvegarde de base de données, mais avant la capture de la relecture de trace est démarrée, la réception WAITFOR émis lors de la relecture peut devoir attendre la durée totale de WAITFOR. Événements configurés pour être relus après que la réception de WAITFOR sera bloquée. Cela peut entraîner le compteur de moniteur de performances de requêtes Batch/s pour la relecture de base de données cible quand vous avez déposé à zéro jusqu'à ce que WAITFOR soit terminée. 
 
 Si vous avez besoin d’utiliser le mode de synchronisation et souhaits afin d’éviter ce comportement, vous devez procédez comme suit :
 
1.  Suspendre les bases de données que vous utiliserez en tant que cibles de la relecture.

2.  Autoriser tous les en attente de l’activité à terminer.

3.  Sauvegarder les bases de données et autoriser les sauvegardes à terminer.

4.  Démarrez la capture de trace de relecture distribuée et reprendre la charge de travail normal. 
 
 
## <a name="see-also"></a> Voir aussi  
 [Options de ligne de commande de l’outil d’administration &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md)   
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)   
 [Forum de SQL Server Distributed Replay](https://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [Utilisation de Distributed Replay pour le test de charge de SQL Server – Partie 2](https://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx)   
 [Utilisation de Distributed Replay pour le test de charge de SQL Server – Partie 1](https://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)  
  
  
