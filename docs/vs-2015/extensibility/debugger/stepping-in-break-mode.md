---
title: Schrittausführung im Unterbrechungsmodus | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e185727343cc7b6be144583c22f78b607af2eec0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58962006"
---
# <a name="stepping-in-break-mode"></a>Schrittausführung im Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird beschrieben, den Prozess, der tritt auf, wenn der Debugger im Unterbrechungsmodus ist und Code durchlaufen schrittweise muss:  
  
## <a name="stepping-process"></a>Zum schrittweisen Prozess  
  
1.  Rufen Sie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit [STEPKIND](../../extensibility/debugger/reference/stepkind.md) und [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) Argumente für einen Schritt ausführen.  
  
2.  Wenn der Schritt abgeschlossen ist, Senden einer [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als Beenden-Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
