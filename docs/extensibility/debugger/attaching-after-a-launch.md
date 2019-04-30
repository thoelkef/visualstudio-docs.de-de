---
title: Anfügen nach einem Start | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b0a34505cf32e0e3fd4dc18bfeab4588856dba4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409949"
---
# <a name="attach-after-a-launch"></a>Fügen Sie nach einem Start
Nachdem ein Programm gestartet hat, kann die Debugsitzung die Debug-Engine (DE) um genannte Anwendung anfügen.

## <a name="design-decisions"></a>Entwurfsentscheidungen
 Da die Kommunikation innerhalb einer gemeinsam genutzten Adressraums einfacher ist, müssen Sie zwischen zwei Ansätze für Design auswählen: Legen Sie die Kommunikation zwischen der Debugsitzung und die DE. Oder legen Sie die Kommunikation zwischen dem Code und das Programm. Wählen Sie zwischen den folgenden:

- Wenn sie zum Einrichten der Kommunikation zwischen der Debugsitzung und die DE sinnvoller, wird die Debugsitzung zusammen erstellt die DE, und fordert die DE zum Anfügen an die Anwendung. Dieser Entwurf bewirkt, dass die Debugsitzung und DE zusammen einen Adressraum, und das Runtime-Umgebung und das Programm in einem anderen zusammen.

- Wenn es mehr zum Einrichten der Kommunikation zwischen dem Code und das Programm sinnvoll ist, wird die Laufzeitumgebung die DE zusammen erstellt. Dieser Entwurf lässt das SDM in einen Adressraum und die DE-Laufzeitumgebung und Programm zusammen in einer anderen. Dieser Entwurf ist typisch für einer bereitgestellten Kompatibilitätsrichtlinie, die mit einem Interpreter zum Ausführen von Skripts Sprachen implementiert wird.

    > [!NOTE]
    > Wie die DE für das Programm angefügt wird, ist implementierungsabhängig. Kommunikation zwischen dem Code und das Programm ist auch abhängig von der Implementierung.

## <a name="implementation"></a>Implementierung
 Programmgesteuert, wenn der Sitzungs-Manager (SDM) zuerst empfängt die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das das Programm gestartet wird, ruft der [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md) Methode auf und übergibt es ein [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das später verwendet, um Debugereignisse zurück, das SDM zu übergeben. Die `IDebugProgram2::Attach` -Methode ruft dann die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode. Weitere Informationen zu den SDM wie empfängt die `IDebugProgram2` Benutzeroberfläche, siehe [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md).

 Wenn Ihre DE im gleichen Adressbereich wie das Programm ausführen muss Debuggen Sie: Da die DE in der Regel einen Interpreter gehört, die ein Skript ausgeführt wird die `IDebugProgramNodeAttach2::OnAttach` Methodenrückgabe `S_FALSE`. Die `S_FALSE` Rückgabewert gibt an, dass den anfügungsprozess abgeschlossen.

 Wenn Sie jedoch die DE in den Adressraum, der das SDM ausgeführt wird: die `IDebugProgramNodeAttach2::OnAttach` Methodenrückgabe `S_OK`, oder die [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) Schnittstelle ist nicht an alle implementiert die [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt verknüpft ist, mit dem Programm, das Sie debuggen. In diesem Fall die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) schließlich aufgerufen, um der Anfügevorgang abgeschlossen.

 In letzterem Fall müssen Sie Aufrufen der [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) Methode für die `IDebugProgram2` -Objekt, das übergeben wurde die `IDebugEngine2::Attach` -Methode, Store die `GUID` in der lokalen Anwendung Objekt aus, und dies zurückzugeben `GUID` bei der `IDebugProgram2::GetProgramId` Methode für dieses Objekt anschließend aufgerufen wird. Die `GUID` wird verwendet, um die Anwendung in den verschiedenen Komponenten von Debug eindeutig zu identifizieren.

 Im Fall von der `IDebugProgramNodeAttach2::OnAttach` Methode zurückgeben `S_FALSE`, `GUID` für das Programm die Verwendung dieser Methode übergeben wird, und es ist die `IDebugProgramNodeAttach2::OnAttach` Methode, die festlegt der `GUID` für das Objekt für lokale Programme.

 Die DE ist jetzt für das Programm und bereit ist, senden alle Startereignisse angefügt werden.

## <a name="see-also"></a>Siehe auch
- [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md)
- [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)