---
title: 'Idiaenumsymbolsbyaddr:: Prev | Microsoft-Dokumentation'
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
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4cd0e3df43002d5893ab77870fbb62f4fff9754
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851581"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die vorherige Symbole in der Reihenfolge nach Adresse ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Symbole in der Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Ein Array, das mit gefüllt werden soll [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekte, die die gewünschten Symbole darstellen.  
  
 pceltFetched  
 [out] Gibt die Anzahl der Symbole in der abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` treten keine vorherigen Symbole. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode aktualisiert die Position des Enumerators durch die Anzahl der Elemente abgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



