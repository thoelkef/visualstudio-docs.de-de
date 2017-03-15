---
title: "IDebugPortEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "IDebugPortEvents2-Schnittstelle"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird ein Listener \(in der Regel der Debug\- Manager der Sitzung \[\] oder SDM\) \- Modul eine Debug\- und Programmierung über Prozess\- und \- zerstörung für einen bestimmten Anschluss.  Diese Informationen können verwendet werden, um eine Ansicht der Prozesse und Echtzeit Darstellung der Programme, die auf dem Port ausgeführt werden.  
  
## Syntax  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio normalerweise implementiert diese Schnittstelle, um Benachrichtigungen über Programm und \- zerstörung zu empfangen.  Ein Debuggen Modul kann diese Schnittstelle implementieren, um auch für solche Ereignisse Port zu überwachen.  
  
## Hinweise für Aufrufer  
 Alle [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Schnittstellen können für eine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>\-Schnittstelle abgefragt werden.  Anschließend wird die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A>\-Methode für `IDebugPortEvents2` in der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>\-Schnittstelle aufgerufen, um eine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>\-Schnittstelle abzurufen.  Schließlich wird die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>\-Methode in der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>\-Schnittstelle aufgerufen, um die Ereignisse von der [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)\-Methode zu senden.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle sind die Methode von `IDebugPortEvents2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Sendet Ereignisse, die die Erstellung und Zerstörung von Prozessen und von Programmen auf dem Port beschreiben.|  
  
## Hinweise  
 `IDebugPortEvents2` wird auch vom SDM auf Testprogrammen verwendet, die in einen Prozess ausgeführt wird, der bereits gedebuggt wird.  
  
 Ereignisse werden an den Anschluss SDM über diese Schnittstelle übergeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)