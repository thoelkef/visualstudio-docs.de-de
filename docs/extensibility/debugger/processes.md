---
title: "Prozesse | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] verarbeitet"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Prozesse
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger ein **Prozess**:  
  
-   Ist ein Container für eine Gruppe von Programmen.  Es ist eng mit einem Fenster Prozess, der ein Container für eine Gruppe von Threads ist.  
  
-   Kann sich, Bezeichner oder physischen Bezeichner des Namens identifizieren.  
  
-   Es können alle laufenden Programme \(und ihre Threads\) auflisten.  
  
-   Kann den Anschluss, die er ausgeführt wird und der Computer beschreiben, der er enthalten ist.  
  
-   Kann eine oder mehrere Programme erstellen, eines der Programme zu beenden, die sie erstellt oder bewirkt ein Programm anzuhalten.  
  
-   Wird von einer [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)\-Schnittstelle dargestellt, die erstellt wird, wenn der Prozess gestartet wurde.  Ein Vorgang wird von jedem der Debug\- Manager der Sitzung \(SDM\) oder [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)gestartet.  
  
 Das Debuggen kann ein Paket debuggen DE \(Modul\) an einen Prozess anfügen, indem [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)aufruft.  Dies bedeutet, dass für alle DE Programme, die in den Prozess anfügt, die er verarbeiten kann.  Wenn z. B. die Common Language Runtime DE an einen Prozess anfügt, wird sie nur für Programme, die verwalteten Code ausführen.  
  
## Siehe auch  
 [Programs](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug\-Paket](../../extensibility/debugger/debug-package.md)   
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)