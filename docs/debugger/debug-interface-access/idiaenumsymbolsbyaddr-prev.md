---
title: 'Idiaenumsymbolsbyaddr:: Prev | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7edaccc32a6557071aa294884348029d2841f8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Ruft die vorherige Symbole in der Reihenfolge nach Adresse ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Symbole im Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Ein Array, das mit ausgefüllt werden [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekte, die die gewünschten Symbole darstellen.  
  
 pceltFetched  
 [out] Gibt die Anzahl der Symbole in der abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` treten keine vorherigen Symbole. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird die Position des Enumerators aktualisiert, um die Anzahl der abgerufenen Elemente.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)