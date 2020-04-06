---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723541"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Diese Schnittstelle stellt einen laufenden Prozess und seine Programme dar. Diese Schnittstelle ist als Ersatz für mehrere Methoden in der [IDebugProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogram2.md) vorhanden. Es bietet die Kontrolle über alle Programme im Prozess.

> [!NOTE]
> Die Methoden ["Weiter ausführen](../../../extensibility/debugger/reference/idebugprogram2-continue.md) ["](../../../extensibility/debugger/reference/idebugprogram2-execute.md)und ["Schritt"](../../../extensibility/debugger/reference/idebugprogram2-step.md) sind veraltet und sollten nicht mehr verwendet werden. Verwenden Sie stattdessen `IDebugProcess3` die entsprechenden Methoden auf der Schnittstelle.

## <a name="syntax"></a>Syntax

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einem benutzerdefinierten Portanbieter implementiert, um Programme als Gruppe zu verwalten. Wenn Programme als Gruppe verwaltet werden, können Sie deren Ausführung steuern und eine Sprache für einen Ausdrucksevaluator einrichten. Diese Schnittstelle muss vom Portlieferanten implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird in erster Linie vom Sitzungsdebug-Manager (SDM) aufgerufen, um mit einer Gruppe von Programmen zu interagieren, die in diesem Prozess identifiziert wurden.

 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer [IDebugProcess2-Schnittstelle](../../../extensibility/debugger/reference/idebugprocess2.md) auf, um diese Schnittstelle abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den methoden, die von `IDebugProcess3` [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)geerbt wurden, werden die folgenden Methoden implementiert.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Setzt die Ausführung eines Prozesses fort oder tritt sie durch.|
|[Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Beginnt mit der Ausführung eines Prozesses.|
|[Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Führt eine Anweisung oder Anweisung im Prozess vor.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ruft den Grund ab, warum der Prozess zum Debuggen gestartet wurde.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Legt die Hostingsprache fest, damit das Debugmodul den entsprechenden Ausdrucksevaluator laden kann.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Ruft die Sprache ab, die derzeit für diesen Prozess festgelegt ist.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deaktiviert Bearbeiten und Fortfahren (ENC) für diesen Prozess.<br /><br /> Ein benutzerdefinierter Portlieferant implementiert diese Methode `E_NOTIMPL`nicht (sie sollte immer zurückgegeben werden).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Erhalten Sie den ENC-Status für diesen Prozess.<br /><br /> Ein benutzerdefinierter Portlieferant implementiert diese Methode `E_NOTIMPL`nicht (sie sollte immer zurückgegeben werden).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Ruft ein Array eindeutiger Bezeichner für verfügbare Debugmodule ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
