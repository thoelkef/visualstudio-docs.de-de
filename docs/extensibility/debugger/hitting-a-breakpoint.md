---
title: Das Erreichen eines Haltepunkts | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dfdf86124bdaf9160121b7d93263dc1d60425515
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="hitting-a-breakpoint"></a>Das Erreichen eines Haltepunkts
Die folgenden beschreibt den Prozess, bei der Debugging-Modul (DE) einen Haltepunkt trifft, bei der Ausführung oder das schrittweise durchlaufen:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Problembehandlung bei einem Treffer Haltepunkt  
  
1.  Sendet die DE ein [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Schnittstelle als eine **EVENT_SYNC_STOP**.  
  
2.  Ruft die Sitzungs-Debug-Manager (SDM) [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) Haltepunkt abgerufen, die erreicht wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)