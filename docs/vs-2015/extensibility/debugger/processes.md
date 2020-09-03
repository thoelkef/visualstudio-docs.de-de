---
title: Prozesse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153665"
---
# <a name="processes"></a>Prozesse
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ist ein **Prozess**:  
  
- Ist ein Container für einen Satz von Programmen. Sie ähnelt einem Windows-Prozess, bei dem es sich um einen Container für eine Gruppe von Threads handelt.  
  
- Kann sich selbst anhand des Namens, Bezeichners oder physischen Bezeichners identifizieren.  
  
- Kann alle ausgelaufenden Programme (und deren Threads) auflisten.  
  
- Kann sich selbst, den Port, in dem er ausgeführt wird, und den Computer, der ihn enthält, beschreiben.  
  
- Kann ein oder mehrere Programme erstellen, alle erstellten Programme beenden oder ein Programm beenden.  
  
- Wird durch eine [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) -Schnittstelle dargestellt, die beim Starten des Prozesses erstellt wird. Ein Prozess wird entweder vom Sitzungs-Debug-Manager (SDM) oder vom [launchangeh](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)alten gestartet.  
  
  Das Debugpaket kann eine Debug-Engine (de) durch Aufrufen von [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)an einen Prozess anfügen. Dies bedeutet, dass der de an alle möglichen Programme angefügt wird, die in dem Prozess ausgeführt werden, der verarbeitet werden kann. Wenn z. b. der Common Language Runtime de an einen Prozess angefügt wird, wird er nur an Programme angefügt, die verwalteten Code ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programme](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Paket Debuggen](../../extensibility/debugger/debug-package.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [Launchangeh alten](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)
