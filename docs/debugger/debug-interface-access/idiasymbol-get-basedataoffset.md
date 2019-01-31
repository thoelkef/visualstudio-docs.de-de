---
title: IDiaSymbol::get_baseDataOffset | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb2ff5ed-9293-4c37-9741-654058b571c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64b77c08d98535666f109610b618eac00b24aaf7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069004"
---
# <a name="idiasymbolgetbasedataoffset"></a>IDiaSymbol::get_baseDataOffset
Ruft den Offset für die Basisdaten ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_baseDataOffset(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `DWORD` , die den Offset für die Basisdaten enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)