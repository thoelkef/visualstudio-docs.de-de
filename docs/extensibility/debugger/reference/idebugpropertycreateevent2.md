---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
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
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "IDebugPropertyCreateEvent2-Schnittstelle"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird durch das Debugmodul \(DE Debuggen\) zum Manager der Sitzung \(SDM\) gesendet wenn das Element eine Eigenschaft erstellt, die einem bestimmten Dokument zugeordnet ist.  
  
## Syntax  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft erstellt wurde.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  Diese Schnittstelle wird implementiert, wenn DE eine Eigenschaft erstellt hat, die mit einem Skript zugeordnet ist, das geladen oder erstellt wurde und das Skript in der IDE angezeigt werden muss.  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, um eine Eigenschaft wurde erstellt.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wird, wenn sie dem Programm verknüpft ist, das gedebuggt wird.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle sind die Methode der `IDebugPropertyCreateEvent2`\-Schnittstelle an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ruft die neue Eigenschaft ab.|  
  
## Hinweise  
 Wenn eine Eigenschaft ein bestimmtes Dokument oder ein Skript verfügt zugeordnet werden, kann dieses Ereignis in das DE SDM senden, um das **Skriptdokumente** Fenster mit dem Namen des Dokuments zu aktualisieren.  Das SDM ruft [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) mit dem Argument `guidDocument` auf, um `VARIANT` abzurufen, das einen [IUnknown](/visual-cpp/atl/iunknown) Zeiger enthält.  Das SDM ruft [QueryInterface](/visual-cpp/atl/queryinterface) für diesen Zeiger auf, um die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Schnittstelle abzurufen, die verwendet wird, um das **Skriptdokumente** Fenster zu aktualisieren.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)