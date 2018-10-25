---
title: Benachrichtigen des Ports | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a45882b1410391843b9e98dcce6e963774c15dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868299"
---
# <a name="notify-the-port"></a>Benachrichtigen Sie den port
Nach dem Starten eines Programms, muss der Port, wie folgt benachrichtigt werden:  
  
1. Bei ein Port einen neuen Knoten für die Anwendung empfängt, sendet er ein Programm Erstellungsereignis zurück an die Debug-Sitzung. Das Ereignis enthält eine Schnittstelle, die Anwendung darstellt.  
  
2. Die Debugsitzung fragt die Anwendung für den Bezeichner einer Debug-Engine (DE), die zum Anfügen können.  
  
3. Die Debugsitzung überprüft, um festzustellen, ob die DE in der Liste der zulässigen des (Datenverschlüsselungsstandard) dieses Programm ist. Die Debugsitzung ruft diese Liste ab, aus der Projektmappe active programmeinstellungen, ursprünglich durch das debugpaket übergeben.  
  
    Die DE in der Liste der zulässigen befinden muss, andernfalls die DE für das Programm nicht angefügt.  
  
   Programmgesteuert, wenn ein Port zuerst einen neuen Knoten für die Anwendung empfängt, erstellt es ein [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, um die Anwendung darstellen.  
  
> [!NOTE]
>  Dies sollte nicht mit verwechselt werden die `IDebugProgram2` Schnittstelle, die später von der Debug-Engine (DE) erstellt.  
  
 Der Port sendet eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Programm Erstellungsereignis an die sitzungsbasierter Debug-Manager (SDM) mithilfe einer COM- `IConnectionPoint` Schnittstelle.  
  
> [!NOTE]
>  Dies sollte nicht mit verwechselt werden die `IDebugProgramCreateEvent2` -Schnittstelle, die später von der DE gesendet wird.  
  
 Zusammen mit der Ereignisschnittstelle selbst, der Port sendet die [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), und [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Schnittstellen, die den Port darstellen, zu verarbeiten, und Programmieren Sie, bzw. Die SDM-Aufrufe [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) um die GUID des DE abzurufen, die das Programm zu debuggen können. Die GUID war ursprünglich abgerufene der [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle.  
  
 Das SDM überprüft, um festzustellen, ob die DE in der Liste der zulässigen DEs ist. Das SDM ruft diese Liste ab, aus der Projektmappe active programmeinstellungen, ursprünglich durch das debugpaket übergeben. Die DE in der Liste der zulässigen befinden muss, andernfalls wird an das Programm nicht angefügt werden.  
  
 Nachdem die Identität des DE bekannt ist, ist das SDM bereit für die Verbindung mit dem Programm.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)   
 [Anfügen nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)