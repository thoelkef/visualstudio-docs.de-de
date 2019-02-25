---
title: Die Programmsteuerung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98c63d2eff11997a37d27f71d01403b59f276e2b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679137"
---
# <a name="program-control"></a>Programmsteuerung
Treten in Visual Studio debuggen, die alle der folgenden schrittweises Durchlaufen und Fortsetzen von Routinen auf Programmebene:

-   Festlegen der nächsten Anweisung an, festlegen den Computer, also, auf die nächste Anweisung in einer bestimmten Frame-Umgebung ausgeführt werden soll

-   Ausgeführt, d. h. weiterhin im schrittweisen Modus beenden

-   Schrittweises durchlaufen für die nächste Anweisung

-   Mit dem aktuellen Modus für die schrittweise Ausführung fortsetzen

-   Anhalten von Threads enthalten, die von der Anwendung

-   Fortsetzen von Threads enthalten, die von der Anwendung

> [!NOTE]
>  Anzeigen der Aufrufliste wird auf der Threadebene implementiert. Sie müssen zum Aufzählen der Frame-Informationen beim Anzeigen der Aufrufliste für einen Thread alle Methoden implementieren die [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Schnittstelle.

## <a name="methods-of-program-control"></a>Methoden der Programmsteuerung
 Die folgende Tabelle zeigt die Methoden der [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , die für eine minimale funktionale Debug-Engine (DE) und Steuerung der Ausführung implementiert werden muss.

|Methode|Beschreibung|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Weiterhin die Ausführung aller Threads, die von einem Programm aus dem Status "beendet" enthalten. Für die Steuerung der Ausführung erforderlich.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Weiterhin die Ausführung aller Threads, die von einem Programm aus dem Status "beendet" enthalten. Für die Steuerung der Ausführung erforderlich.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt Schritt für den angegebenen Thread an. Wird weiter ausgeführt alle anderen Threads, die von der Anwendung enthalten sind. Für die Steuerung der Ausführung erforderlich.|

 Für Multithreadprogramme, müssen Sie auch implementieren die [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) -Methode und alle Methoden der [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [Ausführung und Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)