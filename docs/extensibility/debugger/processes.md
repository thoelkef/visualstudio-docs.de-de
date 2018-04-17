---
title: Prozesse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 75230740e84bb6660629b38e84df56fa8e5c1856
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="processes"></a>Prozesse
Im Hinblick auf die Architektur des Debuggers einen **Prozess**:  
  
-   Ist ein Container für eine Gruppe von Programmen. Es ist eng an einen Windows-Prozess, der einen Container für eine Gruppe von Threads darstellt.  
  
-   Können sich nach Name, Bezeichner oder physischen Bezeichner identifizieren.  
  
-   Alle ausgeführten Programme (und deren Threads) können aufgelistet werden.  
  
-   Beschreiben, durch selbst, den Port an, den es ausgeführt wird und dem Computer, der es enthält.  
  
-   Können, erstellen Sie eine oder mehrere Programme beenden eines der Programme, die sie erstellt oder dazu führen, dass ein Programm zu beenden.  
  
-   Dargestellt durch eine [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) -Schnittstelle, die erstellt wird, wenn der Prozess gestartet wird. Ein Prozess wird gestartet, indem entweder der Sitzungs-Manager (SDM) oder [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Das debugpaket kann ein Debugging-Modul (DE) an einen Prozess anfügen, durch den Aufruf [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md). Dies bedeutet, dass die DE fügt alle möglichen Programme, die im Prozess, den er behandeln kann ausgeführt. Wenn die common Language Runtime DE an einen Prozess angehängt wird, fügt ihn z. B. nur für Programme, die verwalteten Code ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug-Paket](../../extensibility/debugger/debug-package.md)   
 [Debuggen des Datenbankmoduls](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)