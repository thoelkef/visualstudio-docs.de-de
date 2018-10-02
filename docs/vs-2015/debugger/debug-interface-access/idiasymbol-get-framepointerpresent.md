---
title: 'Idiasymbol:: Get_framepointerpresent | Microsoft-Dokumentation'
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
- IDiaSymbol::get_framePointerPresent method
ms.assetid: d036090a-1651-454d-9130-b798f58ba053
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41989d8432085bb4f779b602f1939a9c9fc58cb3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515486"
---
# <a name="idiasymbolgetframepointerpresent"></a>IDiaSymbol::get_framePointerPresent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_framepointerpresent](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-framepointerpresent).  
  
Ruft ein Flag, das angibt, ob der Frame-Pointer vorhanden ist. Verwenden, wenn die [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) nastaven NA hodnotu `SymTagFunction`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_framePointerPresent(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out]] Gibt `TRUE` gibt zurück, wenn der Frame-Pointer vorhanden, andernfalls ist, `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



