---
title: Schrittausführung im Unterbrechungsmodus | Microsoft-Dokumentation
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
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4400bcbecce322185ec514e6d05ac9a37e27fdde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749098"
---
# <a name="stepping-in-break-mode"></a>Schrittausführung im Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird beschrieben, den Prozess, der tritt auf, wenn der Debugger im Unterbrechungsmodus ist und Code durchlaufen schrittweise muss:  
  
## <a name="stepping-process"></a>Zum schrittweisen Prozess  
  
1.  Rufen Sie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit [STEPKIND](../../extensibility/debugger/reference/stepkind.md) und [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) Argumente für einen Schritt ausführen.  
  
2.  Wenn der Schritt abgeschlossen ist, Senden einer [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als Beenden-Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)

