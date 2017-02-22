---
title: "IDebugCoreServer2 | Microsoft Docs"
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
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "IDebugCoreServer2-Schnittstelle"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um Informationen von einem Server auf einem Computer im Netzwerk abzurufen und anzuzeigen.  
  
## Syntax  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um einen Server zu repräsentieren.  Jede Instanz von Visual Studio wird eine Instanz dieser Schnittstelle.  
  
## Hinweise für Aufrufer  
 Ein benutzerdefinierter Port lieferant empfängt diese Schnittstelle in einem Aufruf von [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Ein Debuggen Modul kann diese Schnittstelle durch einen Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) \(der [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)zurückgibt, eine Schnittstelle, die von `IDebugCoreServer2`abgeleitet ist\) indirekt abrufen.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugCoreServer2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ruft den Namen und den Attributen eines Computers ab.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ruft den Namen eines Computers ab.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ruft den Anschlusslieferanten ab, der von einem Computer vorhanden ist.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ruft einen Port ab, der bereits von einem Computer vorhanden ist.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Erstellt einen Enumerator für alle Ports auf einem Computer.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Erstellt einen Enumerator für alle Anschlusslieferanten auf einem Computer.|  
|[GetMachineUtilities\_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ruft die Computer Hilfsprogramme für einen Computer ab.|  
  
## Hinweise  
 Diese Schnittstelle wird von Visual Studio verwendet, um die Prozesse zu durchsuchen, die auf Computer im Netzwerk ausgeführt werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)