---
title: "Anhängen an ein Programm direkt | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c528925e323e4cff5784365e3097cc7f5f414963
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-directly-to-a-program"></a>Anhängen an ein Programm direkt
Gehen Sie Benutzer, die zum Debuggen von Programmen in einem Prozess, der bereits in der Regel ausgeführt werden soll:  
  
1.  Wählen Sie in der IDE die **Prozesse Debuggen** Befehl die **Tools** Menü.  
  
     Die **Prozesse** Dialogfeld wird angezeigt.  
  
2.  Wählen Sie einen Prozess aus, und klicken Sie auf die **Anfügen** Schaltfläche.  
  
     Die **an den Prozess anhängen** im angezeigten Dialogfeld Auflisten aller Debugmodule (DEs) auf dem Computer installiert.  
  
3.  Geben Sie den Datenverschlüsselungsstandard DEs zu verwenden, um den ausgewählten Prozess zu debuggen, und klicken Sie dann auf **OK**.  
  
 Das debugpaket startet eine Debugsitzung und die Liste der DEs an sie übergeben. Die Debugsitzung wiederum übergibt diese Liste, zusammen mit einer Rückruffunktion, um den ausgewählten Prozess, und fordert dann den Prozess zum Aufzählen von seinen Programmen ausgeführten.  
  
 Programmgesteuert, als Antwort auf die Anforderung des Benutzers, das debugpaket instanziiert die Sitzungs-Debug-Manager (SDM) und die Liste der ausgewählten DEs an sie. Zusammen mit der Liste aus, übergibt das debugpaket die SDM ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) Schnittstelle. Das debugpaket übergibt die Liste der DEs an den ausgewählten Prozess, durch den Aufruf [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Ruft die SDM dann [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) auf den Port an, die im Prozess ausgeführten Programme aufgelistet werden.  
  
 Ab diesem Punkt jedes Debugmodul angefügt ist, um ein Programm genau wie im [Anfügen eines starten Sie nach dem](../../extensibility/debugger/attaching-after-a-launch.md), mit zwei Ausnahmen.  
  
 Aus Effizienzgründen DEs, die implementiert werden, um einen Adressraum für das SDM freigeben werden so gruppiert, damit jeder DE hat eine Reihe von Programme aus, die angefügt wird. In diesem Fall [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) Aufrufe [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) und übergibt ein Array von Programmen an.  
  
 Die zweite Ausnahme ist, dass die Startereignisse per einer bereitgestellten Kompatibilitätsrichtlinie Anhängen an ein Programm, die bereits ausgeführt wird, ist nicht in der Regel das punktereignis Eintrag enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Senden von Startereignisse nach einem starten](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)