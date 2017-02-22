---
title: "IDebugPort2 | Microsoft Docs"
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
  - "IDebugPort2"
helpviewer_keywords: 
  - "IDebugPort2-Schnittstelle"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Anschluss Debuggen auf einem Computer dar.  
  
## Syntax  
  
```  
IDebugPort2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle, um einen Debugbuild Anschluss auf einem Computer darzustellen.  
  
 Wenn der Anschluss das Senden von Ereignissen Port unterstützt, muss er die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> auch Schnittstelle implementieren, um eine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>\-Schnittstelle zu unterstützen, die wiederum die [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)\-Schnittstelle bereitstellt.  
  
## Hinweise für Aufrufer  
 Aufrufe von [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) oder [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) diese Schnittstelle zurückgeben, den angeforderten Anschluss darstellt.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugPort2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Gibt den Namen des Anschlusses zurück.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Gibt den Port Bezeichner zurück.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Gibt die Anforderung zurück, die verwendet wird, um einen Port \(falls verfügbar\).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Gibt den Anschlusslieferanten für diesen Port zurück.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Gibt eine Schnittstelle für Bezeichner des Prozesses anhand des Prozesses zurück.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Listet alle Prozesse auf, die für einen Port ausgeführt werden.|  
  
## Hinweise  
 Der lokale Ports ermöglicht den Zugriff auf alle Prozesse und Programme, die auf dem lokalen Computer ausgeführt werden.  Andere Ports stellen möglicherweise einen seriellen Kabelanschluss CE\-basierten Gerät zu einem Fenster oder eine Netzwerkverbindung mit einem Computer Nicht DCOM dar.  Die `IDebugPort2`\-Schnittstelle wird verwendet, um den Namen und den Bezeichner eines Ports zu suchen, listen alle ausgeführten Verarbeitung auf dem Port und stellt Funktionen zum Starten und Beenden von Prozessen auf dem Port bereit.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)