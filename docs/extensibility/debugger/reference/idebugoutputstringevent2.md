---
title: "IDebugOutputStringEvent2 | Microsoft Docs"
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
  - "IDebugOutputStringEvent2"
helpviewer_keywords: 
  - "IDebugOutputStringEvent2-Schnittstelle"
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird durch das Debugmodul \(DE Debuggen\) zum Manager der Sitzung \(SDM\) gesendet um eine Zeichenfolge auszugeben.  
  
## Syntax  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um eine Zeichenfolge in den **Ausgabe** Fenster der IDE zu senden.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, um eine Zeichenfolge in den **Ausgabe** Fenster zu senden.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wird, wenn sie dem Programm verknüpft ist, das gedebuggt wird.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle sind die Methode von `IDebugOutputStringEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ruft die anzeigbare Meldung.|  
  
## Hinweise  
 Beispielsweise aus nicht verwaltetem Code ausgegeben werden soll, kann die Zeichenfolge stammen, wenn das Programm, das gedebuggt wird, eine Zeichenfolge in die Win32\-Funktion `OutputDebugString` sendet.  Diese Zeichenfolge wird nach dem Senden abgefangen und DE SDM als `IDebugOutputStringEvent2`\-Ereignis.  
  
 Verwenden Sie [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) , um eine Nachricht zu senden, die eine Benutzerantwort verlangt.  
  
 Verwenden Sie [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) , um eine Fehlermeldung gesendet werden, die keine Antwort erforderlich ist.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)