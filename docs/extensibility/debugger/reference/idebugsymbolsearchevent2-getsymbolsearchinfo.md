---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird von einem Ereignishandler, um Ergebnisse zu einem Symbol ladevorgang abzurufen.  
  
## Syntax  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### Parameter  
 `pModule`  
 \[out\]  Ein Objekt IDebugModule3, das das Modul darstellt, für das die Symbole geladen wurden.  
  
 `pbstrDebugMessage`  
 \[in, out\]  Gibt eine Zeichenfolge zurück, die alle Fehlermeldungen vom Modul enthält.  Wenn kein Fehler vorliegt, enthält diese Zeichenfolge einfach den Namen des Moduls, ist jedoch niemals leer.  
  
> [!NOTE]
>  \[C\+\+\] kann nicht `pbstrDebugMessage``NULL` sein und muss mit `SysFreeString`freigegeben werden.  
  
 `pdwModuleInfoFlags`  
 \[out\]  Eine Kombination von Flags aus der [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)\-Enumeration, der angibt, ob Symbole geladen wurden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Wenn ein Handler für das [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)\-Ereignis empfängt, nachdem der Versuch, Debugsymbole für ein Modul geladen festgelegt ist, kann der Handler thismethod aufrufen, um die Ergebnisse dieser Auslastung zu bestimmen.  
  
## Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)