---
title: 'Idiaenumsymbols:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3cc898d989c345ba7691252562fac820eec1c18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924109"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Ruft ein Symbol mithilfe eines Indexes ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 [in] Der Index der [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt abgerufen werden sollen. Der Index befindet sich im Bereich von 0 bis `count`-1 und, in dem `count` wird zurückgegeben, durch die [idiaenumsymbols:: Get_count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) Methode.  
  
 Symbol  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das das gewünschte Symbol darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)