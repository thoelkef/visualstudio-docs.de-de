---
title: "IDebugSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2"
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird durch das Debugmodul \(DE\) gesendet, um anzugeben, dass die Debugsymbole für ein Modul, das gedebuggt wird, geladen wurden.  
  
## Syntax  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um zu melden, dass die Symbole einem Modul geladen wurden.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, um zu melden, dass die Symbole einem Modul geladen wurden.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als sie angefügt haben dem Programm, das gedebuggt wurde.  
  
## Methoden in die Vtable\-Reihenfolge  
 Die `IDebugSymbolSearchEvent2`\-Schnittstelle macht die folgende Methode.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Ruft Informationen über die Ergebnisse der Symbolsuche ab.|  
  
## Hinweise  
 Dieses Ereignis wird auch wenn die Symbole, die Übertragung zu ladende fehlgeschlagen sind.  Das Aufrufen von `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` kann der Handler dieses Ereignisses können Sie bestimmen, ob das Modul eigentlich alle Symbole verfügt.  
  
 Visual Studio verwendet in der Regel dieses Ereignis, um den Status der geladenen Symbolen im **Module** Fenster zu aktualisieren.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)