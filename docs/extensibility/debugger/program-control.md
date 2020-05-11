---
title: Programmsteuerung | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738225"
---
# <a name="program-control"></a>Programmsteuerung
Beim Visual Studio-Debuggen werden alle folgenden Schritt- und Fortlierungsroutinen auf Programmebene ausgeführt:

- Festlegen der nächsten Anweisung, d. d. a. Festlegen der nächsten Anweisung, die in einer bestimmten Frameumgebung ausgeführt werden soll

- Ausführen, d. a. das Fortsetzen des Stepping-Modus

- Schritt zur nächsten Anweisung

- Fortsetzung des aktuellen Schrittmodus

- Anhalten der im Programm enthaltenen Threads

- Wiederaufnahme der im Programm enthaltenen Threads

> [!NOTE]
> Das Anzeigen der Aufrufliste wird auf Threadebene implementiert. Um die Frameinformationen beim Anzeigen der Aufrufliste für einen Thread aufzulisten, müssen Sie alle Methoden der [IEnumDebugFrameInfo2-Schnittstelle](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) implementieren.

## <a name="methods-of-program-control"></a>Methoden der Programmsteuerung
 Die folgende Tabelle zeigt die Methoden von [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) die für ein minimal funktionierendes Debugmodul (DE) und eine Ausführungssteuerung implementiert werden müssen.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Führt die Ausführung aller Threads fort, die von einem Programm aus einem angehaltenen Zustand enthalten sind. Erforderlich für die Ausführungssteuerung.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Führt die Ausführung aller Threads fort, die von einem Programm aus einem angehaltenen Zustand enthalten sind. Erforderlich für die Ausführungssteuerung.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt für den angegebenen Thread aus. Führt weiterhin alle anderen Threads aus, die im Programm enthalten sind. Erforderlich für die Ausführungssteuerung.|

 Für Multithreadprogramme müssen Sie auch die [IDebugProgram2::EnumThreads-Methode](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) und alle Methoden der [IEnumDebugThreads2-Schnittstelle](../../extensibility/debugger/reference/ienumdebugthreads2.md) implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungskontrolle und Zustandsbewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
