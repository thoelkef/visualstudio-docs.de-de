---
title: "Programmsteuerelement | Microsoft Docs"
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
  - "Debuggen [Debuggen SDK], Steuerung der Ausführung"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Programmsteuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In Visual Studio\-Debugging treten alle nachfolgenden tretenden und fortfahrenden Routinen auf der Ebene Programm auf:  
  
-   Die folgende Anweisung festlegen d. h. den Computer an die nächste Anweisung festlegen, in einer bestimmten Rahmen Umgebungen ausgeführt werden soll  
  
-   d. h. sie beginnend weiterhin Auschecken aus treten Modus beenden  
  
-   Zur nächsten Anweisung befinden  
  
-   Mit dem aktuellen Modus Schritt fortsetzen  
  
-   Die Threads angehalten werden vom Programm enthalten  
  
-   Die Threads fort vom Programm enthalten  
  
> [!NOTE]
>  Die Aufrufliste angezeigt wird, wird der Thread auf Anwendungsebene implementiert.  Um die Rahmeninformationen auflisten, wenn Sie die Aufrufliste für einen Thread, müssen Sie alle Methoden der [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)\-Schnittstelle implementieren.  
  
## Methoden des Programm\-Steuerelements  
 In der folgenden Tabelle werden die Methoden von [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) an, die für ein funktionales minimal Modul \(Debug\) und DE Execution Control implementiert werden müssen.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDebugProgram2::Ausführen](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Setzt die Ausführung aller Threads fort, die durch ein Programm aus einem Beendet enthalten sind.  Erforderlich für Execution Control.|  
|[IDebugProgram2::Fahren Sie fort](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Setzt die Ausführung aller Threads fort, die durch ein Programm aus einem Beendet enthalten sind.  Erforderlich für Execution Control.|  
|[IDebugProgram2::Schritt](../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Einzelschritt für den angegebenen Thread aus.  Setzt die Ausführung aller anderen Threads fort, die durch das Programm enthalten sind.  Erforderlich für Execution Control.|  
  
 In Multithreaded Programme müssen Sie die [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)\-Methode und alle Methoden der [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) auch Schnittstelle implementieren.  
  
## Siehe auch  
 [Steuerung der Ausführung und Status Bewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)