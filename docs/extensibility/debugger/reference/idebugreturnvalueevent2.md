---
title: "IDebugReturnValueEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReturnValueEvent2"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2"
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReturnValueEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird durch das Senden Debugmodul \(DE Debuggen\) zum Manager der Sitzung \(SDM\) oder nachdem er über eine Funktion aufgetreten ist.  
  
## Syntax  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um den Rückgabewert einer Funktion, out aus oder hergestellt wurde.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, um den Rückgabewert einer Funktion.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wird, wenn sie dem Programm verknüpft ist, das gedebuggt wird.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle sind die Methode von `IDebugReturnValueEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Ruft den Wert ab, der für das schrittweise Ausführen einer Funktion zurückgegeben wird.|  
  
## Hinweise  
 Der Wert, der von einer Funktion zurückgegeben wird, kann abgerufen werden, indem [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)aufruft.  Der zurückgegebene Wert wird im **Auto** Fenster.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)