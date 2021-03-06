---
title: PDO::getAvailableDrivers | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8e34675ccd92ae714117a41198518cb7ec28afb
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604849"
---
# <a name="pdogetavailabledrivers"></a>PDO::getAvailableDrivers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Retourne un tableau des pilotes PDO dans votre installation PHP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array PDO::getAvailableDrivers ();  
```  
  
## <a name="return-value"></a>Valeur retournée  
Tableau avec la liste des pilotes PDO.  
  
## <a name="remarks"></a>Notes   
Le nom du pilote PDO est utilisé dans PDO::__construct pour créer une instance PDO.  
  
PDO::getAvailableDrivers n’est pas besoin d’être implémenté par les pilotes PHP. Pour plus d’informations sur cette méthode, consultez la documentation de PHP.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a> Exemple  
  
```  
<?php  
print_r(PDO::getAvailableDrivers());  
?>  
```  
  
## <a name="see-also"></a> Voir aussi  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
