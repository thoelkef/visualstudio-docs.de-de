---
title: Erreichen eines halte Punkts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152698"
---
# <a name="hitting-a-breakpoint"></a>Erreichen eines Haltepunkts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird der Prozess beschrieben, wenn die Debug-Engine (de) einen Haltepunkt beim Ausführen oder Ausführen eines Schrittes erreicht:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Problembehandlung eines Treffer halte Punkts  
  
1. Der de sendet eine [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Schnittstelle als **EVENT_SYNC_STOP**.  
  
2. Der Session Debug Manager (SDM) ruft [IDebugBreakpointEvent2::: enumbreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) auf, um den Treffer Haltepunkt zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
