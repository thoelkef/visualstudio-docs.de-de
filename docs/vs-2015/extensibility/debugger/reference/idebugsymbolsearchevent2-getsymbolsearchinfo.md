---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 398fa692e79b5cbe1e532cb51d7d23fc12fec0b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946556"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wird aufgerufen, von einem Ereignishandler, um Ergebnisse zu einem Symbol-Load-Prozess abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `pModule`  
 [out] Ein IDebugModule3-Objekt, das das Modul für das die Symbole geladen wurden darstellt.  
  
 `pbstrDebugMessage`  
 [in, out] Gibt eine Zeichenfolge, die alle Fehlermeldungen aus dem Modul enthält. Wenn kein Fehler vorliegt, klicken Sie dann diese Zeichenfolge enthält nur den Modulnamen, aber sie ist niemals leer.  
  
> [!NOTE]
>  [C++] `pbstrDebugMessage` nicht `NULL` und freigegeben werden müssen, mit `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Eine Kombination von Flags aus der [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Enumeration, der angibt, ob keine Symbole geladen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Ereignishandler empfängt die [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) Ereignis aus, nachdem versucht wird, um Debugsymbole für ein Modul zu laden, kann der Handler für diese Methode, um die Ergebnisse der diese Last zu ermitteln, aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
