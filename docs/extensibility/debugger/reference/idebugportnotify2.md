---
title: "IDebugPortNotify2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "IDebugPortNotify2-Schnittstelle"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle registriert oder hebt die Registrierung eines Programms mit dem Port gedebuggt werden kann, den sie ausgeführt wird.  
  
## Syntax  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle, um das Hinzufügen und Entfernen von Programmen auf dem Port zu unterstützen.  Sie wird i. d. R. in demselben Objekt implementiert, das die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle implementiert.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [QueryInterface](/visual-cpp/atl/queryinterface) auf der `IDebugPort2`\-Schnittstelle wird von dieser Schnittstelle zurück.  Außerdem wird ein Aufruf [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) gibt diese Schnittstelle zurück.  Ein Debuggen Modul kann diese Schnittstelle als Parameter an [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)sehen.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugPortNotify2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registriert ein Programm, das dem Port gedebuggt werden kann, den er ausgeführt wird.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Hebt die Registrierung eines Programms vom Port gedebuggt werden kann, den er ausgeführt wird.|  
  
## Hinweise  
 Sofern ein Multithreaded Anschluss verfügt eine Möglichkeit festzustellen, wann Programme geladen oder entladen werden, muss ein benutzerdefinierter Port lieferant diese Schnittstelle implementieren.  Alle Programme, die für das Debuggen durch einen bestimmten Anschluss geladen werden, werden mithilfe dieser Schnittstelle überwacht.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)