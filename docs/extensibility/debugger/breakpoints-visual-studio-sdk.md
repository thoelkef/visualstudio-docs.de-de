---
title: Haltepunkte (Visual Studio SDK) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 146c8c7e17017a675ad1077d03800328b0d345d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932675"
---
# <a name="breakpoints-visual-studio-sdk"></a>Haltepunkte (Visual Studio SDK)
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