---
title: IDiaSymbol::findSymbolsForAcceleratorPointerTag | Microsoft-Dokumentation
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
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97f60cc0d6b2bc08dd3b1ab8fcaa31decf23ddd5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751524"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Anzahl der Tags von Accelerator-Zeiger in einer C++ AMP-Stub-Funktion zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT findSymbolsForAccleratorPointerTag (   
   DWORD             tagValue,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Parameter  
 `tagValue`  
 [in] Der Wert des Zeigers-Tag, für den die symboldatensätze Pointee gefunden werden.  
  
 `ppResult`  
 [out] Ein Zeiger auf ein `IDiaEnumSymbols` Schnittstellenzeiger, der mit dem Ergebnis initialisiert wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



