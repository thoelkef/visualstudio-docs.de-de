---
title: "EVENTATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "EVENTATTRIBUTES-enumeration"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Ereignisattribute an.  
  
## Syntax  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## Mitglieder  
 EVENT\_ASYNCHRONOUS  
 Gibt an, dass das Ereignis asynchron ist und keine Antwort auf das Ereignis benötigt wird.  
  
 EVENT\_SYNCHRONOUS  
 Gibt an, dass das Ereignis synchron ist. Reaktion mittels [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT\_STOPPING  
 Gibt an, dass es sich um ein aufhörendes Ereignis ist.  Muss mit `EVENT_ASYNCHRONOUS` oder `EVENT_SYNCHRONOUS`kombiniert werden.  
  
 EVENT\_ASYNC\_STOP  
 Gibt eine asynchrone aufhörendes Ereignis an.  Es gibt derzeit kein entsprechendes Ereignis.  Dieses Flag ist nur ein Platzhalter.  
  
 EVENT\_SYNCHRONIZATION\_STOP  
 Gibt ein synchrones aufhörendes Ereignis an \(eine Kombination aus `EVENT_SYNCHRONOUS` und `EVENT_STOPPING`\).  Dieser Wert wird von einem Modul \(Debug\) DE aufhörendes wenn ein Ereignis sendet.  Die Antwort wird mithilfe eines Aufrufs von [Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md)oder [Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md)gemacht.  
  
 EVENT\_IMMEDIATE  
 Gibt ein Ereignis an, das sofort an die IDE und synchron gesendet wird.  Dieses Flag wird mit anderen Flags wie `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`oder `EVENT_SYNC_STOP` kombiniert, um den Typ des Ereignisses und den Fakten anzugeben, dass der Mechanismus für die Antwort \(sofern vorhanden\) bekannt ist.  
  
 EVENT\_EXPRESSION\_EVALUATION  
 Das Ereignis ist ein Ergebnis der Ausdrucksauswertung.  
  
## Hinweise  
 Diese Werte werden in den `dwAttrib`[Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)\-Parameter der Methode übergeben.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)