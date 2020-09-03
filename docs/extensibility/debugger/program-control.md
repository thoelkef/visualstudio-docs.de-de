---
title: Programmsteuerung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738225"
---
# <a name="program-control"></a>Programmsteuerung
Beim Debuggen in Visual Studio erfolgen alle folgenden Schritt-und fortsetzenden Routinen auf der Programmebene:

- Festlegen der nächsten Anweisung, d. h. Festlegen des Computers auf die nächste Anweisung, die in einer bestimmten Frame Umgebung ausgeführt werden soll

- Ausführen von, d. h. fortsetzen des Fortschritt Modus

- Schritt der nächsten Anweisung

- Fortfahren mit dem aktuellen Schritt Modus

- Anhalten der im Programm enthaltenen Threads

- Fortsetzen der im Programm enthaltenen Threads

> [!NOTE]
> Das Anzeigen der-aufrufsstapel ist auf Thread Ebene implementiert. Um die Frame Informationen beim Anzeigen der-aufrufsstapel für einen Thread aufzulisten, müssen Sie alle Methoden der [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Schnittstelle implementieren.

## <a name="methods-of-program-control"></a>Methoden der Programmsteuerung
 In der folgenden Tabelle sind die Methoden von [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) aufgeführt, die für eine minimal funktionale Debug-Engine (de) und die Ausführungs Steuerung implementiert werden müssen.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Setzt die Ausführung aller Threads in einem Programm in einem beendeten Zustand fort. Erforderlich für die Ausführungs Steuerung.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Setzt die Ausführung aller Threads in einem Programm in einem beendeten Zustand fort. Erforderlich für die Ausführungs Steuerung.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt für den angegebenen Thread aus. Setzt die Ausführung aller anderen im Programm enthaltenen Threads fort. Erforderlich für die Ausführungs Steuerung.|

 Für Multithreadprogramme müssen Sie auch die [IDebugProgram2:: enumthreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) -Methode und alle Methoden der [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) -Schnittstelle implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungs Steuerung und Zustands Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
