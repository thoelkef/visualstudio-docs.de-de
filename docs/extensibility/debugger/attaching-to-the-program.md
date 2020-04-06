---
title: Anfügen an das Programm | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739239"
---
# <a name="attach-to-the-program"></a>An das Programm anhängen
Nachdem Sie Ihre Programme mit dem entsprechenden Port registriert haben, müssen Sie den Debugger an das Programm anfügen, das Sie debuggen möchten.

## <a name="choose-how-to-attach"></a>Wählen Sie, wie Sie
 Es gibt drei Möglichkeiten, wie der Sitzungsdebug-Manager (SDM) versucht, an das zu debuggende Programm anzuhängen.

1. Für Programme, die vom Debugmodul über die [LaunchSuspended-Methode](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) gestartet werden (z. B. typisch für interpretierte Sprachen), ruft das SDM die [IDebugProgramNodeAttach2-Schnittstelle](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) von dem [IDebugProgramNode2-Objekt](../../extensibility/debugger/reference/idebugprogramnode2.md) ab, das dem Anfügen des Programms zugeordnet ist. Wenn das SDM `IDebugProgramNodeAttach2` die Schnittstelle abrufen kann, ruft das SDM die [OnAttach-Methode](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) auf. Die `IDebugProgramNodeAttach2::OnAttach` Methode `S_OK` gibt zurück, um anzugeben, dass sie nicht an das Programm angefügt wurde und dass andere Versuche unternommen werden können, an das Programm anzuhängen.

2. Wenn das SDM die [IDebugProgramEx2-Schnittstelle](../../extensibility/debugger/reference/idebugprogramex2.md) von dem Programm abrufen kann, an das angefügt wird, ruft das SDM die [Attach-Methode](../../extensibility/debugger/reference/idebugprogramex2-attach.md) auf. Dieser Ansatz ist typisch für Programme, die vom Portanbieter remote gestartet wurden.

3. Wenn das Programm nicht `IDebugProgramNodeAttach2::OnAttach` über `IDebugProgramEx2::Attach` die oder-Methoden angefügt werden kann, lädt das `CoCreateInstance` SDM das Debugmodul (wenn nicht bereits geladen), indem es die Funktion aufruft, und ruft dann die [Attach-Methode](../../extensibility/debugger/reference/idebugengine2-attach.md) auf. Dieser Ansatz ist typisch für Programme, die lokal von einem Portlieferanten gestartet werden.

    Es ist auch möglich, dass ein `IDebugEngine2::Attach` benutzerdefinierter Portlieferant die Methode `IDebugProgramEx2::Attach` in der Implementierung der Methode durch den benutzerdefinierten Portlieferanten aufruft. In der Regel startet der benutzerdefinierte Portlieferant in diesem Fall das Debugmodul auf dem Remotecomputer.

   Die Anlage wird erreicht, wenn der Sitzungsdebug-Manager (SDM) die [Attach-Methode](../../extensibility/debugger/reference/idebugengine2-attach.md) aufruft.

   Wenn Sie Ihre DE im gleichen Prozess wie die zu debuggende Anwendung ausführen, müssen Sie die folgenden Methoden von [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)implementieren:

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Nachdem `IDebugEngine2::Attach` die Methode aufgerufen wurde, führen Sie `IDebugEngine2::Attach` die folgenden Schritte in der Implementierung der Methode aus:

1. Senden Sie ein [IDebugEngineCreateEvent2-Ereignisobjekt](../../extensibility/debugger/reference/idebugenginecreateevent2.md) an das SDM. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).

2. Rufen Sie die [GetProgramId-Methode](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) für das [IDebugProgram2-Objekt](../../extensibility/debugger/reference/idebugprogram2.md) auf, das an die `IDebugEngine2::Attach` Methode übergeben wurde.

     Dadurch wird `GUID` eine zurückgegeben, die zum Identifizieren des Programms verwendet wird. Der `GUID` muss in dem Objekt gespeichert werden, das das lokale Programm `IDebugProgram2::GetProgramId` für die DE `IDebugProgram2` darstellt, und es muss zurückgegeben werden, wenn die Methode auf der Schnittstelle aufgerufen wird.

    > [!NOTE]
    > Wenn Sie `IDebugProgramNodeAttach2` die Schnittstelle implementieren, `GUID` wird das `IDebugProgramNodeAttach2::OnAttach` Programm an die Methode übergeben. Dies `GUID` wird für die `GUID` von `IDebugProgram2::GetProgramId` der Methode zurückgegebene Anwendung verwendet.

3. Senden Sie ein [IDebugProgramCreateEvent2-Ereignisobjekt,](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) um `IDebugProgram2` das SDM darüber zu informieren, dass das lokale Objekt erstellt wurde, um das Programm für die DE darzustellen. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Dies ist `IDebugProgram2` nicht dasselbe Objekt, das an die `IDebugEngine2::Attach` Methode übergeben wurde. Das zuvor `IDebugProgram2` übergebene Objekt wird nur vom Port erkannt und ist ein separates Objekt.

## <a name="see-also"></a>Weitere Informationen
- [Start-basierte Anlage](../../extensibility/debugger/launch-based-attachment.md)
- [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)
