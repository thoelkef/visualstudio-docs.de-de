---
title: "IDebugPortEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2"
helpviewer_keywords: 
  - "IDebugPortEx2-Schnittstelle"
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht den Debug\- Manager der Sitzung \(SDM\) Programme und Prozesse, die auf einen Port gesteuert werden.  
  
## Syntax  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)implementiert.  
  
## Hinweise für Aufrufer  
 Das SDM ruft [QueryInterface](/visual-cpp/atl/queryinterface) auf der `IDebugPort2`\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugPortEx2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Startet eine ausführbare Datei.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Setzt die Ausführung eines Prozesses fort.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Beendet einen Prozess.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ruft die Prozess\-ID des Anschlusses selbst ab.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ruft ein Objekt ab, das mit einem Programm unter dem Knoten zugeordnet ist.|  
  
## Hinweise  
 Diese Schnittstelle wird normalerweise zwischen dem SDM und dem benutzerdefinierten Anschlusslieferanten privat.  
  
 Wenn es erforderlich ist, kann eine Debug\- Modul \(DE\) nach dieser Schnittstelle auf der [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle zu suchen, die [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) übergeben wird und [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) verwenden, um das Programm zu starten.  Dies ist jedoch nicht erforderlich und DE ausführen kann, was sie ausführen muss, um die Anforderung zu starten programm.  
  
## Anforderungen  
 Header: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)