---
title: Start-basierte Anlage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d05f0b8d8fd0190391da831351b65d873eac4efc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="launch-based-attachment"></a>Start-basierte Anlage
Start-basierte das Anfügen an ein Programm wird automatisch wiederhergestellt. Wenn der Hostprozess für das Programm durch die SDM gestartet wird, folgt Launch-basierte Anlage einen Pfad, der ähnlich dem Konzept der manuellen Methode. Informationen finden Sie unter [Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Der Prozess anfügen  
 Der Hauptunterschied ist die Abfolge der Ereignisse, die nach der **Anfügen** wie folgt aufrufen:  
  
1.  Senden einer **IDebugEngineCreateEvent2** Ereignisobjekt, das SDM. Weitere Informationen finden Sie unter [Ereignisse senden](../../extensibility/debugger/sending-events.md).  
  
2.  Rufen Sie die `IDebugProgram2::GetProgramId` Methode für die **IDebugProgram2** Schnittstelle übergeben, um die **Anfügen** Methode.  
  
3.  Senden einer **IDebugProgramCreateEvent2** Ereignisobjekt, das SDM benachrichtigen, die der lokalen **IDebugProgram2** Objekt, das Sie erstellt wurde, um das Programm de darstellen.  
  
4.  Senden einer [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Ereignisobjekt, das SDM benachrichtigen, dass ein neuer Thread für den Prozess erstellt wird, die gestartet.  
  
## <a name="see-also"></a>Siehe auch  
 [Senden die erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)   
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)