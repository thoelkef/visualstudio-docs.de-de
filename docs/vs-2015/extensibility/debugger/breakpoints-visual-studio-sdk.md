---
title: Haltepunkte (Visual Studio SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39c13271bad984291f609ef45505549855bee99f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146422"
---
# <a name="breakpoints-visual-studio-sdk"></a>Haltepunkte (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es gibt drei Arten von Haltepunkten: Ausstehend "," gebunden und Fehler.  
  
 **Ein ausstehender Haltepunkt:**  
  
- Ist eine Abstraktion, die alle einen Haltepunkt für eine oder mehrere Codekontexte in einem oder mehreren Programmen binden erforderlichen Informationen enthält. Jedes Mal überprüft Ursachencode zum Laden eines Programms, gedebuggt werden, die Debug-Engine alle ausstehenden Haltepunkte, um festzustellen, ob sie gebunden werden können.  
  
   Ein ausstehender Haltepunkt selbst nie bindet an Code, aber stattdessen erfasst und alle gebundenen Breakpoints enthalten, die es generiert hat.  
  
- Wird durch dargestellt eine [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstelle.  
  
  **Einen gebundenen Haltepunkt:**  
  
- Eine Abstraktion für einen Haltepunkt ist zugeordnet oder an einem einzigen Kontext gebunden. Jede gebundene Haltepunkt wird als Reaktion auf ein ausstehender Haltepunkt generiert. Ein ausstehender Haltepunkt kann jedoch mehr als einen gebundenen Haltepunkt generieren.  
  
   Wenn Code entladen wird, kann ein gebundener Haltepunkt aufgehoben und verworfen werden.  
  
- Wird durch dargestellt eine [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Schnittstelle.  
  
  **Ein Haltepunkt Fehler:**  
  
- Ist eine Abstraktion zum Beschreiben eines Fehlers beim Versuch, einen ausstehenden Haltepunkt in einen Codekontext zu binden. Ein Haltepunkt auf Fehler wird entweder einen Fehler Standort oder an den Haltepunktausdruck selbst beschrieben. Weitere Informationen finden Sie unter [Binden von Haltepunkten](../../extensibility/debugger/binding-breakpoints.md).  
  
   Der haltepunktfehler kann entweder eine Fehler- oder eine Warnung sein.  
  
- Wird durch dargestellt eine [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
