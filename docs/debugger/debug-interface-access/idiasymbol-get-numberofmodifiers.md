---
title: IDiaSymbol::get_numberOfModifiers | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61ff7431-1994-4f7e-a182-1817f16f60a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 911e5f405dd7889378b62d9ec5bef3c943d3c85f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875792"
---
# <a name="idiasymbolgetnumberofmodifiers"></a>IDiaSymbol::get_numberOfModifiers
Ruft die Anzahl der Modifizierer, die in den ursprünglichen Typ angewendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_numberOfModifiers(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `DWORD` , der angibt, dass der Anzahl der Modifizierer, die in den ursprünglichen Typ angewendet werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)