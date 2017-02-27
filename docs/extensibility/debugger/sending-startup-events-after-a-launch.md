---
title: "Senden Startereignisse nach einem starten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Startup-Ereignisse"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Senden Startereignisse nach einem starten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Einmal wird das Debugmodul \(DE\) in das Programm sendet er eine Reihe von Ereignissen Start wieder der Debugsitzung angefügt.  
  
 Ereignisse schickten Debuggen auf Start der Sitzung umfassen Folgendes zurück:  
  
-   Ein Modul Builds wird.  
  
-   Ein Programm Builds wird.  
  
-   Threaderstellungs\- und \-Modulladeereignisse.  
  
-   Ein vollständiges Ereignis der Auslastung, wenn der Code geladen ist und bereiten, um vor ausgeführt werden, bevor gesendet, aber jeder Code ausgeführt wird  
  
    > [!NOTE]
    >  Wenn dieses Ereignis fortgesetzt wird, werden globale Variablen und Startroutine initialisiert werden.  
  
-   Folgende anderen Thread erstellungs\- und \- Modul ladeereignisse.  
  
-   Ein Einstiegspunkt Ereignis, das signalisiert, dass das Programm den Haupteinstiegspunkt erreicht hat, z. B. **Hauptframe** oder `WinMain`.  Dieses Ereignis wird i. d. R. nicht gesendet, wenn DE mit einem Programm angefügt wird, das bereits ausgeführt wird.  
  
 Programmgesteuert sendet DE Debuggen zunächst den Manager der Sitzung \(SDM\) eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)\-Schnittstelle, die ein Modul Builds Ereignis darstellt, das [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), gefolgt von einem Programm Builds Ereignis darstellt.  
  
 Dies wird in der Regel von einem oder mehreren [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Thread erstellungs\-Ereignis\- und [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) Modul ladeereignissen.  
  
 Wenn der Code geladen wird und die Ausführung vorbereitet, aber vor jeder Code ausgeführt wird, sendet das Ereignis ein vollständiges SDM DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Auslastung.  Wenn das Programm nicht bereits ausgeführt wird, sendet signalisiert wird, und ein DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Einstiegspunkt, dass das Programm den Haupteinstiegspunkt erreicht hat und ist zum Debuggen beginnen.  
  
## Siehe auch  
 [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md)   
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)