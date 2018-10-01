---
title: Schrittausführung im Unterbrechungsmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0721dcfe857f5c21aab634d02c29e864870c440b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514912"
---
# <a name="stepping-in-break-mode"></a>Schrittausführung im Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Einzelschrittausführung im Unterbrechungsmodus](https://docs.microsoft.com/visualstudio/extensibility/debugger/stepping-in-break-mode).  
  
Im folgenden wird beschrieben, den Prozess, der tritt auf, wenn der Debugger im Unterbrechungsmodus ist und Code durchlaufen schrittweise muss:  
  
## <a name="stepping-process"></a>Zum schrittweisen Prozess  
  
1.  Rufen Sie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit [STEPKIND](../../extensibility/debugger/reference/stepkind.md) und [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) Argumente für einen Schritt ausführen.  
  
2.  Wenn der Schritt abgeschlossen ist, Senden einer [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als Beenden-Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)

