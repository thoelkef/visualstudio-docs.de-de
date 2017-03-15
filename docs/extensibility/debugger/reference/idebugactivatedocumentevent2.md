---
title: "IDebugActivateDocumentEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugActivateDocumentEvent2"
helpviewer_keywords: 
  - "IDebugActivateDocumentEvent2-Schnittstelle"
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Das Debugmodul \(DE\) verwendet diese Schnittstelle, um eine zu ladende Dokument anzufordern.  
  
## Syntax  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, wenn eine Quelldatei muss geöffnet sein.  Diese Schnittstelle wird nur von Debugsymbolinformationen auf Module implementiert, die mit Skripts arbeiten oder ist Teil interpreter.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM das [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen\).  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, wenn eine Quelldatei geöffnet sein muss.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugActivateDocumentEvent2`an.  
  
|Methoden|Beschreibung|  
|--------------|------------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Ruft das Dokument ab, um zu aktivieren.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Ruft den Dokumentenkontext ab, der die Position innerhalb des Dokuments beschreibt.|  
  
## Hinweise  
 Ein typisches Szenario, in dem diese Schnittstelle ist, wenn ein Analysefehler im Skriptcode auf einer HTML\-Seite auftritt, das Skript DE sendet diese Schnittstelle zum SDM, sodass das Dokument mit dem Analysefehler angezeigt werden kann.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)