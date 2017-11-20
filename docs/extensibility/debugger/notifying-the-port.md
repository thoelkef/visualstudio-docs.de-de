---
title: Benachrichtigen den Port | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91bedf387fe86c2bf2fefb34e643e581a37c15bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="notifying-the-port"></a>Benachrichtigen den Port
Nach dem Starten eines Programms, muss der Port, wie folgt darüber informiert werden:  
  
1.  Wenn ein Port einen neuen Knoten für die Anwendung empfängt, sendet er ein Programm Erstellungsereignis zurück an die Debugsitzung an. Das Ereignis enthält eine Schnittstelle, die Anwendung darstellt.  
  
2.  Die Debugsitzung fragt das Programm für den Bezeichner des Debugmoduls (DE), die zum Anfügen können.  
  
3.  Die Debugsitzung überprüft, um festzustellen, ob die DE in der Liste der zulässigen Datenverschlüsselungsstandard dieses Programm ist. Die Debugsitzung ruft diese Liste ab, aus der Projektmappe aktive programmeinstellungen, die ursprünglich von der debugpaket übergeben.  
  
     DE muss auf die Liste der zulässigen, da sonst die DE nicht an das Programm angefügt.  
  
 Wenn ein Port zuerst einen neuen Knoten für die Anwendung empfängt programmgesteuert erstellt ein [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, um die Anwendung darzustellen.  
  
> [!NOTE]
>  Dies sollte nicht mit verwechselt werden die `IDebugProgram2` Schnittstelle, die später von der Debugging-Modul (DE) erstellt wurden.  
  
 Der Port sendet eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Erstellungsereignis zurück an den Sitzung Debug-Manager (SDM) über einen COM-Programm `IConnectionPoint` Schnittstelle.  
  
> [!NOTE]
>  Dies sollte nicht mit verwechselt werden die `IDebugProgramCreateEvent2` -Schnittstelle, die später von der DE gesendet wird.  
  
 Zusammen mit der Ereignis-Oberfläche selbst, der Port sendet die [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), und [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Schnittstellen, die den Port darstellen, zu verarbeiten, und Programmieren Sie, bzw.. Ruft die SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) um die GUID des DE abzurufen, die das Programm debuggen können. Die GUID abgerufen wurde ursprünglich von der [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle.  
  
 Die SDM überprüft, um festzustellen, ob die DE in der Liste der zulässigen DEs ist. Die SDM ruft diese Liste ab, aus der Projektmappe aktive programmeinstellungen, die ursprünglich von der debugpaket übergeben. DE in der Liste der zulässigen befinden muss, andernfalls wird an das Programm nicht angefügt werden.  
  
 Nachdem die Identität des DE bekannt ist, ist die SDM bereit für die Verbindung an das Programm.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)   
 [Nach einem Start Anfügen](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)