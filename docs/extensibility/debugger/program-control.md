---
title: Die Programmsteuerung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c227f38c926cb6d764ddf47541b8bd744eb6f7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102089"
---
# <a name="program-control"></a>Programmsteuerung
In Visual Studio auftreten, Debuggen, die alle der folgenden schrittweise durchlaufen und Fortsetzen von Routinen auf der Ebene der Anwendung:  
  
-   Festlegen der nächsten Anweisung an, d. h. Einrichten des Computers für die nächste Anweisung in einer bestimmten Frame-Umgebung ausgeführt werden  
  
-   Ausführen, d. h. weiterhin schrittweisen Modus beenden  
  
-   Schrittweises durchlaufen für die nächste Anweisung  
  
-   Mit dem aktuellen Modus für die schrittweise Ausführung fortsetzen  
  
-   Die von der Anwendung enthaltenen Threads anhalten  
  
-   Die Threads, die von der Anwendung enthaltenen fortsetzen  
  
> [!NOTE]
>  Die Aufrufliste anzuzeigen, wird auf der Threadebene implementiert. Um die Frame-Informationen aufgezählt werden beim Anzeigen der Aufrufliste für einen Thread, müssen Sie die Methoden der implementieren die [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Schnittstelle.  
  
## <a name="methods-of-program-control"></a>Methoden der Programmsteuerung  
 Die folgende Tabelle zeigt die Methoden der [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , muss für eine minimal funktionale Debugging-Modul (Deutschland) und die Steuerung der Ausführung implementiert werden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Weiterhin die Ausführung aller Threads, die von einem Programm aus dem Status "beendet" enthalten. Für die Steuerung der Ausführung erforderlich.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Weiterhin die Ausführung aller Threads, die von einem Programm aus dem Status "beendet" enthalten. Für die Steuerung der Ausführung erforderlich.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt auf den angegebenen Thread. Alle anderen Threads, die von der Anwendung enthaltenen läuft. Für die Steuerung der Ausführung erforderlich.|  
  
 Für Multithreadprogramme, müssen Sie auch implementieren die [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) -Methode und alle Methoden der [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)