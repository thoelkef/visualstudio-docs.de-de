---
title: 'Idiasymbol:: Get_haslongjump | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83a6588a7d217321f7f6cba37faf73fbe0359608
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904387"
---
# <a name="idiasymbolgethaslongjump"></a>IDiaSymbol::get_hasLongJump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, das angibt, ob die Funktion eine Verwendung von enthält die [Longjmp](http://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f) Befehl (mit gekoppelten eine [Setjmp](http://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2) Befehl bilden die C-Stil-Methode der Ausnahmebehandlung).  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Gibt `TRUE` , wenn die Funktion enthält einen `longjmp` Befehl; andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_hassetjump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](http://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f)   
 [setjmp](http://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2)



