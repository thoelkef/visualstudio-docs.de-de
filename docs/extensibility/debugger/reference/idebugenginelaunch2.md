---
title: "IDebugEngineLaunch2 | Microsoft Docs"
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
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "IDebugEngineLaunch2-Schnittstelle"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird von einem Modul \(Debug\) DE zum Starten und Programme zu beenden.  
  
## Syntax  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von benutzerdefinierten DE implementiert, wenn sie besondere Anforderungen für Starten eines Prozesses verfügt, der nicht durch einen benutzerdefinierten Port vollständig behandelt werden kann.  Dies ist normalerweise der Fall, wenn DE Teil eines Interpreters ist und der Prozess, der gedebuggt wird, ein Skript ist: muss zuerst der Interpreter ausgeführt werden, und anschließend wird das Skript geladen und gestartet.  Ein Port kann der Interpreter starten, aber das Skript \(der eine Sonderbehandlung erfordert möglicherweise wird DE eine Rolle verfügt\).  Diese Schnittstelle wird implementiert, wenn es nur eindeutige Anforderungen für Starten eines Programms vorhanden ist, das einen benutzerdefinierten Port nicht behandeln kann.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird vom Debugbuild Manager der Sitzung \(SDM\) aufgerufen, wenn das SDM diese Schnittstelle von der Schnittstelle abrufen kann [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) \(mit QueryInterface\).  Wenn diese Schnittstelle abgerufen werden kann, weiß das SDM, dass DE besondere Anforderungen verfügt und ruft diese Schnittstelle auf, um das Programm den Port, anstatt auf Start zu öffnen.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugEngineLaunch2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Startet einen Prozess mithilfe DEs.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Setzt Prozessausführung fort.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Beendet einen Prozess.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)