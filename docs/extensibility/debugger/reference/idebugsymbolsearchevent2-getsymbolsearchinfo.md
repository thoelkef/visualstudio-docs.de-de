---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 518429149ad1d997b860e486f3db4e519ef42cae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Wird aufgerufen, von einem Ereignishandler zum Abrufen von Ergebnissen zu einem Symbol Ladevorgangs.  
  
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
 [out] Ein IDebugModule3-Objekt, das für das Modul für das die Symbole geladen wurden.  
  
 `pbstrDebugMessage`  
 [in, out] Gibt eine Zeichenfolge, enthält alle Fehlermeldungen aus dem Modul zurück. Wenn kein Fehler vorliegt, diese Zeichenfolge wird einfach den Modulnamen enthalten, aber sie ist niemals leer.  
  
> [!NOTE]
>  [C++] `pbstrDebugMessage` nicht `NULL` und freigegeben werden muss, mit `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Eine Kombination aus Flags aus der [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Enumeration, der angibt, ob Symbole geladen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Ereignishandler empfängt die [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) Ereignis, wenn versucht wird, um Debugsymbole für ein Modul zu laden, der Handler kann rufen Sie diese Methode, um die Ergebnisse der diese Last zu ermitteln.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)