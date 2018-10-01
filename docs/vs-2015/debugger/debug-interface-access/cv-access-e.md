---
title: CV_access_e | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5096c90727a1c8ffcf871853d1f59610a2baff37
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512140"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CV_access_e](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/cv-access-e).  
  
Gibt den Bereich, Sichtbarkeit (Zugriffsebene) von Memberfunktionen und Variablen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_access_e {   
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
 [Idiasymbol:: Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)



