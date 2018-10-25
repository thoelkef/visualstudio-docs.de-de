---
title: Direktes Anfügen an ein Programm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de07b2fc8846bd24bb3e4483c78eb339d9d49e4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817547"
---
# <a name="attaching-directly-to-a-program"></a>Direktes Anfügen an ein Programm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gehen Sie Benutzer, die beim Debuggen von Programmen in einem Prozess, der bereits, in der Regel ausgeführt wird möchten:  
  
1. Wählen Sie in der IDE die **Debugprozesse** Befehl die **Tools** Menü.  
  
    Das Dialogfeld **Prozesse** wird angezeigt.  
  
2. Wählen Sie einen Prozess aus, und klicken Sie auf die **Anfügen** Schaltfläche.  
  
    Die **an den Prozess anhängen** im angezeigten Dialogfeld auflisten alle Debug-Engines (DEs), auf dem Computer installiert.  
  
3. Geben Sie die DEs zu verwenden, um den ausgewählten Prozess debuggen, und klicken Sie dann auf **OK**.  
  
   Das debugpaket startet eine Debugsitzung, und die Liste der DEs übergeben. Die Debugsitzung wiederum übergibt diese Liste zusammen mit der eine Callback-Funktion, um den ausgewählten Prozess, und fordert dann der Vorgang zum Auflisten von seinen Programmen ausgeführten.  
  
   Programmgesteuert, wird als Antwort auf Anforderung des Benutzers, ein das debugpaket sitzungsbasierter Debug-Manager (SDM) instanziiert und die Liste der ausgewählten DEs übergeben. Zusammen mit der Liste aus, übergibt das debugpaket das SDM ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) Schnittstelle. Das debugpaket übergibt die Liste der DEs an den ausgewählten Prozess, durch den Aufruf [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Klicken Sie dann aufruft, das SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) auf den Port an, die im Prozess ausgeführten Programme aufgelistet werden.  
  
   Ab diesem Zeitpunkt auf jede Debug-Engine angefügt ist, an ein Programm genau wie im [Anfügen einer starten Sie nach dem](../../extensibility/debugger/attaching-after-a-launch.md), mit zwei Ausnahmen.  
  
   Aus Effizienzgründen DEs, die implementiert werden, wenn Sie einen Adressraum für das SDM freigeben werden so gruppiert, sodass jede DE enthält eine Reihe von Programmen, die sie beim Hinzufügen. In diesem Fall [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) Aufrufe [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) und übergibt ein Array von Programmen für das Anfügen an.  
  
   Die zweite Ausnahme ist, dass die Startereignisse, die per einer bereitgestellten Kompatibilitätsrichtlinie Anfügen an ein Programm, das bereits ausgeführt wird nicht in der Regel das punktereignis Eintrag enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Senden von Startereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)

