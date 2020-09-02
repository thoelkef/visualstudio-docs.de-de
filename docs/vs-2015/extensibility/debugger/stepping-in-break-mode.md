---
title: Schrittweise im Break-Modus | Microsoft-Dokumentation
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
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423360"
---
# <a name="stepping-in-break-mode"></a>Schrittausführung im Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird der Prozess beschrieben, der auftritt, wenn sich der Debugger im Break-Modus befindet und den Code schrittweise durchlaufen muss:  
  
## <a name="stepping-process"></a>Schritt Prozess  
  
1. Ruft [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit den Argumenten [stepkind](../../extensibility/debugger/reference/stepkind.md) und [stepunit](../../extensibility/debugger/reference/stepunit.md) auf, um einen Schritt auszuführen.  
  
2. Wenn der Schritt abgeschlossen ist, senden Sie ein [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als anhalteereignis.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
