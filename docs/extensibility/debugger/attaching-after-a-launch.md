---
title: Anfügen nach einem Start | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739284"
---
# <a name="attach-after-a-launch"></a>Anfügen nach einem Start
Nach dem Starten eines Programms ist die Debugsitzung bereit, das Debugmodul (DE) an dieses Programm anzuhängen.

## <a name="design-decisions"></a>Entwurfsentscheidungen
 Da die Kommunikation innerhalb eines freigegebenen Adressraums einfacher ist, müssen Sie zwischen zwei Entwurfsansätzen wählen: Festlegen der Kommunikation zwischen der Debugsitzung und der DE. Oder legen Sie die Kommunikation zwischen der DE und dem Programm fest. Wählen Sie zwischen den folgenden Optionen:

- Wenn es sinnvoller ist, die Kommunikation zwischen der Debugsitzung und der DE einzurichten, erstellt die Debugsitzung die DE mit und fordert die DE auf, an das Programm anzuhängen. Bei diesem Entwurf werden die Debugsitzung und DE in einem Adressraum und die Laufzeitumgebung und das Programm in einem anderen Zusammenlaufraum zusammengefügt.

- Wenn es sinnvoller ist, die Kommunikation zwischen der DE und dem Programm einzurichten, erstellt die Laufzeitumgebung die DE mit. Bei diesem Entwurf werden das SDM in einem Adressraum und die DE-, Laufzeitumgebung und das Programm in einem anderen zusammen belassen. Dieser Entwurf ist typisch für eine DE, die mit einem Interpreter implementiert wird, um Skriptsprachen auszuführen.

    > [!NOTE]
    > Wie die DE an das Programm angefügt wird, ist implementierungsabhängig. Die Kommunikation zwischen der DE und dem Programm ist ebenfalls implementierungsabhängig.

## <a name="implementation"></a>Implementierung
 Wenn der Sitzungsdebug-Manager (SDM) zum ersten Mal das [IDebugProgram2-Objekt](../../extensibility/debugger/reference/idebugprogram2.md) empfängt, das das gestartete Programm darstellt, ruft er programmgesteuert die [Attach-Methode](../../extensibility/debugger/reference/idebugprogram2-attach.md) auf und übergibt ein [IDebugEventCallback2-Objekt,](../../extensibility/debugger/reference/idebugeventcallback2.md) das später verwendet wird, um Debugereignisse an das SDM zurückzugeben. Die `IDebugProgram2::Attach` Methode ruft dann die [OnAttach-Methode](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) auf. Weitere Informationen dazu, wie das `IDebugProgram2` SDM die Schnittstelle empfängt, finden Sie [unter Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md).

 Wenn Ihre DE im gleichen Adressraum wie das Programm ausgeführt werden muss, das Sie debuggen: Da die `IDebugProgramNodeAttach2::OnAttach` DE `S_FALSE`in der Regel Teil eines Interpreters ist, der ein Skript ausführt, gibt die Methode zurück. Die `S_FALSE` Rückgabe gibt an, dass der Anfügevorgang abgeschlossen wurde.

 Wenn jedoch die DE im Adressraum des SDM `IDebugProgramNodeAttach2::OnAttach` ausgeführt `S_OK`wird: die Methode gibt zurück , oder die [IDebugProgramNodeAttach2-Schnittstelle](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) wird auf dem [IDebugProgramNode2-Objekt,](../../extensibility/debugger/reference/idebugprogramnode2.md) das dem Programm zugeordnet ist, das Sie debuggen, überhaupt nicht implementiert. In diesem Fall wird die [Attach-Methode](../../extensibility/debugger/reference/idebugengine2-attach.md) schließlich aufgerufen, um den Attach-Vorgang abzuschließen.

 Im letzteren Fall müssen Sie die [GetProgramId-Methode](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) für das Objekt aufrufen, das `IDebugProgram2` an `IDebugEngine2::Attach` die Methode übergeben wurde, die `GUID` im lokalen Programmobjekt speichern und diese `GUID` zurückgeben, wenn die `IDebugProgram2::GetProgramId` Methode anschließend für dieses Objekt aufgerufen wird. Der `GUID` wird verwendet, um das Programm über die verschiedenen Debugkomponenten hinweg eindeutig zu identifizieren.

 Im Fall der `IDebugProgramNodeAttach2::OnAttach` `S_FALSE`zurücksendenden `GUID` Methode wird die für das Programm zu `IDebugProgramNodeAttach2::OnAttach` verwendende Methode `GUID` an diese Methode übergeben, und es ist die Methode, die die für das lokale Programmobjekt festlegt.

 Die DE ist nun an das Programm angefügt und bereit, alle Startereignisse zu senden.

## <a name="see-also"></a>Weitere Informationen
- [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Benachrichtigung über den Hafen](../../extensibility/debugger/notifying-the-port.md)
- [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)
