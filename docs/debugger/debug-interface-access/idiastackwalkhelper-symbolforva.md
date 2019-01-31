---
title: 'Idiastackwalkhelper:: Symbolforva | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a859fc41252fc6f6d8e99ecbaa881cd07ffd6134
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026756"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Ruft ab, das Symbol, das die angegebene virtuelle Adresse enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `va`  
 [in] Die virtuelle Adresse, die im angeforderten Symbol enthalten ist. Das Symbol muss eine `SymTagFunctionType` (ein Wert aus der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration).  
  
 `ppSymbol`  
 [out] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das Symbol an der angegebenen Adresse darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)