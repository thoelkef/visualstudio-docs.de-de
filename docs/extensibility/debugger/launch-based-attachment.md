---
title: Startbasiertes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 518a3f804298df6c0af98a6e5d2a6d851b645aee
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231703"
---
# <a name="launch-based-attachment"></a>Startbasiertes
Startbasiertes an ein Programm erfolgt automatisch. Wenn der Hostprozess für das Programm durch die SDM gestartet wird, folgt startbasiertes einen Pfad, mit der manuellen Anlage Methode ähnelt. Weitere Informationen finden Sie unter [Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Der Prozess anfügen  
 Der Hauptunterschied ist die Abfolge der Ereignisse, die nach der **Anfügen** wie folgt aufrufen:  
  
1.  Senden einer **IDebugEngineCreateEvent2** Event-Objekt, das SDM. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
2.  Rufen Sie die `IDebugProgram2::GetProgramId` Methode für die **IDebugProgram2** Schnittstelle zu übergeben, um die **Anfügen** Methode.  
  
3.  Senden einer **IDebugProgramCreateEvent2** Event-Objekt, das SDM zu benachrichtigen, die der lokalen **IDebugProgram2** Objekt wurde erstellt, um die Anwendung für das DE darstellen.  
  
4.  Senden einer [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Ereignisobjekt, dem SDM benachrichtigen, dass es sich bei ein neuer Thread für den Prozess erstellt wird, die gestartet.  
  
## <a name="see-also"></a>Siehe auch  
 [Senden Sie die erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)   
 [Aktivieren Sie zu debuggenden Programm](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)