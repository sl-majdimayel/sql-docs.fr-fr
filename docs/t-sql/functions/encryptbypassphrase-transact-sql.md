---
title: ENCRYPTBYPASSPHRASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYPASSPHRASE
- ENCRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTBYPASSPHRASE function
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], ENCRYPTBYPASSPHRASE function
ms.assetid: f8dbb9e6-94d6-40d7-8b38-6833a409d597
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1548684a3c2e749e20b6bd9b8a01be272fabb196
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681147"
---
# <a name="encryptbypassphrase-transact-sql"></a>ENCRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Chiffrer des données avec un mot de passe à l'aide de l'algorithme TRIPLE DES avec une longueur de clé de 128 bits.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EncryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'cleartext' | @cleartext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *passphrase*  
 Expression relative au mot de passe à partir de laquelle générer une clé symétrique.  
  
 @passphrase  
 Variable de type **nvarchar**, **char**, **varchar**, **binary**, **varbinary** ou **nchar** qui contient une phrase secrète à partir de laquelle générer une clé symétrique.  
  
 *cleartext*  
 Texte clair à chiffrer.  
  
 @cleartext  
 Variable de type **nvarchar**, **char**, **varchar**, **binary**, **varbinary** ou **nchar** contenant le texte en clair. Sa taille maximale est de 8 000 octets.  
  
 *add_authenticator*  
 Indique si un authentificateur sera chiffré avec le texte en clair. 1 si un authentificateur est ajouté. **int**.  
  
 @add_authenticator  
 Indique si un hachage est chiffré avec le texte clair.  
  
 *authenticator*  
 Données dont l'authentificateur est dérivé. **sysname**.  
  
 @authenticator  
 Variable qui contient les données dont l'authentificateur est dérivé.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary** d’une taille maximale de 8 000 octets.  
  
## <a name="remarks"></a>Notes   
 Une expression relative au mot de passe est un mot de passe qui comporte des espaces. L'avantage d'utiliser une expression relative au mot de passe est qu'il est plus facile de mémoriser une phrase qui a un sens plutôt qu'une longue chaîne de caractères.  
  
 Cette fonction ne vérifie pas la complexité des mots de passe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant met à jour un enregistrement de la table `SalesCreditCard` et chiffre la valeur du numéro de carte de crédit stocké dans la colonne `CardNumber_EncryptedbyPassphrase`, en utilisant la clé primaire comme authentificateur.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create a column in which to store the encrypted data.  
ALTER TABLE Sales.CreditCard   
    ADD CardNumber_EncryptedbyPassphrase varbinary(256);   
GO  
-- First get the passphrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
    = 'A little learning is a dangerous thing!';  
  
-- Update the record for the user's credit card.  
-- In this case, the record is number 3681.  
UPDATE Sales.CreditCard  
SET CardNumber_EncryptedbyPassphrase = EncryptByPassPhrase(@PassphraseEnteredByUser  
    , CardNumber, 1, CONVERT( varbinary, CreditCardID))  
WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [DECRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbypassphrase-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
