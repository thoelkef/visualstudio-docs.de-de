---
title: 'Idiasymbol:: Get_notreached | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_notReached method
ms.assetid: e44ba922-6cda-40c2-9b62-44e5a8628e63
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdc228f239ae8ed051c90cf8e9ee57a098e49a86
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859892"
---
# <a name="idiasymbolgetnotreached"></a>IDiaSymbol::get_notReached
Ruft ein Flag, das angibt, ob die Funktion oder Bezeichnung nie erreicht wird.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_notReached(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pFlag  
 [out] Gibt `TRUE` , wenn die Funktion oder Bezeichnung nie erreicht wird; andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|Dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)