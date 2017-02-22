---
title: "IDebugCanStopEvent2 | Microsoft Docs"
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
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2-Schnittstelle"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um die Sitzung Debuggen von Manager \(SDM\) anzufordern ob am aktuellen Speicherort des Codes angehalten wird.  
  
## Syntax  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um das Durchlaufen des Quellcodes zu unterstützen.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM das [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen\).  
  
 Die Implementierung dieser Schnittstelle muss den Aufruf des SDM von [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) Modul Debuggen zu vermitteln.  Beispielsweise kann dies mit einer Nachricht geschehen, die für den Thread Nachrichtenverarbeitungs Debuggen des Moduls gesendet wurde, oder das Objekt, das diese Schnittstelle implementiert, kann keinen Verweis auf das Modul Debuggen und für den Aufruf in das Debugmodul mit dem Flag ab, das in `IDebugCanStopEvent2::CanStop`übergeben wurde.  
  
## Hinweise für Aufrufer  
 DE senden kann diese Methode bei jedem DE aufgefordert wird, und die Ausführung von Code. tritt DE  Dieses Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugCanStopEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ruft den Grund für dieses Ereignis ab.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Gibt an, ob das Programm, das gedebuggt wird, an der Position dieses Ereignisses \(beenden und ein Ereignis senden, das den Grund für das Anhalten oder Fortsetzen\) beschreibt derzeit ausgeführt werden soll.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ruft den Dokumentenkontext ab, der die Position dieses Ereignisses beschreibt.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ruft den Kontext des Codes ab, der die Position dieses Ereignisses beschreibt.|  
  
## Hinweise  
 DE sendet diese Schnittstelle, wenn die Benutzer Schritte in einer Funktion und DE keine Debuginformationen gefunden oder dort vorhanden sind, aber keine Debuginformationen DE weiß, wenn der Quellcode für diesen Speicherort angezeigt werden kann.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)