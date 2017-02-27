---
title: "IDebugProcessSecurity | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity-Schnittstelle"
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`IDebugProcessSecurity` wird von einem Anschlusslieferanten implementiert, um den Benutzer, dass das Anfügen an den Prozess Warnung unsicher ist.  
  
## Syntax  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProcessSecurity`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ruft den Benutzernamen des Anschlusslieferanten ab.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Warnt einen Benutzer, der das Anfügen an den Debugprozess unsicher ist.|  
  
## Hinweise  
 Implementieren Sie diese Schnittstelle, um eine Warnung anzuzeigen und dem Benutzer zu ermöglichen, abzubrechen, wenn der Prozess, an den angehängt werden, als unsicher betrachtet werden kann.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ports](../../../extensibility/debugger/ports.md)   
 [Port\-Lieferanten](../../../extensibility/debugger/port-suppliers.md)   
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)