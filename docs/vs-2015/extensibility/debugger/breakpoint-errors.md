---
title: Haltepunktfehler | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e98dc5e4645ac67ecdf5ebb06ecf0f31510202e2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114697"
---
# <a name="breakpoint-errors"></a>Haltepunktfehler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die folgenden beschreibt den Prozess aus, wenn ein Haltepunkt zum Binden an Code versucht jedoch ein Fehler auftritt:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Problembehandlung bei einem Breakpoint-Fehler  
  
1. Die Debug-Engine (DE) sendet ein [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) für die Sitzung Debug-Manager (SDM).  
  
2. Die SDM-Aufrufe [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) um den Haltepunkt Fehler zu erhalten.  
  
3. Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) abzurufenden den ausstehenden Haltepunkt, von dem der Haltepunkt Fehler verursacht wurde.  
  
4. Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) abzurufenden den Grund, warum der Haltepunkt Fehler beim Binden Fehler.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
