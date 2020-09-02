---
title: CV_access_e | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164374"
---
# <a name="cv_access_e"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Bereich der Sichtbarkeit (Zugriffsebene) von Element Funktionen und Variablen an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elemente  
 CV_private  
 Mitglied hat privaten Zugriff.  
  
 CV_protected  
 Mitglied hat geschützten Zugriff.  
  
 CV_public  
 Mitglied hat öffentlichen Zugriff.  
  
## <a name="remarks"></a>Bemerkungen  
 Der `friend` Zugriffsspezifizierer ist hier nicht enthalten, da er in der Regel von nicht-Member-Funktionen verwendet wird, die Zugriff auf private und geschützte Elemente der Klasse haben. Verwenden Sie die [idiasymmetribol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) -Methode, um Symbole mit Zugriff zu suchen `SymTagFriend` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymmetribol:: get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
