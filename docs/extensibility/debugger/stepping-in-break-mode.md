---
title: Ausführen in Einzelschritten im Unterbrechungsmodus | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1cf10254ec4642bd6dd671124d4a0600794de6fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130384"
---
# <a name="stepping-in-break-mode"></a>Ausführen in Einzelschritten im Unterbrechungsmodus
Im folgenden wird erläutert, das auftritt, wenn der Debugger im Unterbrechungsmodus und Code durchlaufen schrittweise muss:  
  
## <a name="stepping-process"></a>Ausführen in Einzelschritten Prozess  
  
1.  Rufen Sie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit [STEPKIND](../../extensibility/debugger/reference/stepkind.md) und [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) Argumente für einen Schritt ausführen.  
  
2.  Wenn der Schritt abgeschlossen ist, senden wir Ihnen eine [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als Stopping-Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)