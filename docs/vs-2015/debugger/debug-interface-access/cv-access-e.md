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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956430"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Bereich, Sichtbarkeit (Zugriffsebene) von Memberfunktionen und Variablen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elements  
 CV_private  
 Element verfügt über privaten Zugriff.  
  
 CV_protected  
 Member hat Zugriff geschützt werden.  
  
 CV_public  
 Element verfügt über öffentlichen Zugriff.  
  
## <a name="remarks"></a>Hinweise  
 Die `friend` Zugriffsspezifizierer ist hier nicht enthalten, da sie in der Regel von nicht-Memberfunktionen verwendet wird, die Zugriff auf private oder geschützte Elemente der Klasse haben. Verwenden der [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) Methode zum Suchen von Symbolen mit `SymTagFriend` Zugriff.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
