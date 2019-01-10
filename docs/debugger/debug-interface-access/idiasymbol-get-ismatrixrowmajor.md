---
title: IDiaSymbol::get_isMatrixRowMajor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c6a149b342c55ea59036edb21a2ea51ba8ebb35
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847242"
---
# <a name="idiasymbolgetismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
Gibt an, ob die Matrix mit Zeilen, die wichtigsten ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_isMatrixRowMajor(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `BOOL` , der angibt, ob die Matrix mit Zeilen, die wichtigsten ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)