---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d96e58f19ae4170430488bc33e454d70944c36af
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Wenn einen entsprechenden Tagwert, gibt diese Methode eine Enumeration von Symbolen, die enthalten sind in dieser Stub-Funktion auf einem angegebenen relativen virtuellen Adresse an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Parameter  
 `tagValue`  
 [in] Der Wert des Zeigers-Tag, für den die Pointee symboldatensätze gefunden werden.  
  
 `rva`  
 [in] Die Rva, die verwendet wird, um die Symbole zu filtern, die die Pointee-Variable mit dem angegebenen Tag-Wert entsprechen.  
  
 `ppResult`  
 [out] Ein Zeiger auf ein `IDiaEnumSymbols` Schnittstellenzeiger auf die mit dem Ergebnis initialisiert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Methode nur auf eine `IDiaSymbol` Schnittstelle, die eine Zugriffstaste Stub-Funktion entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)