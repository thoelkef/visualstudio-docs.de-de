---
title: Breakpoint-Fehler | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147985"
---
# <a name="breakpoint-errors"></a>Haltepunktfehler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird der Prozess beschrieben, wenn ein Breakpoint versucht, eine Bindung an Code herzustellen, aber fehlschlägt:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Problembehandlung bei Haltepunkt Fehlern  
  
1. Die Debug-Engine (de) sendet ein [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) an den Sitzungs-Debug-Manager (SDM).  
  
2. Der SDM ruft [IDebugBreakpointErrorEvent2:: geterrorbreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) auf, um den Fehler Haltepunkt zu erhalten.  
  
3. Der SDM ruft [IDebugErrorBreakpoint2:: getpdingbreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) auf, um den ausstehenden Haltepunkt zu erhalten, von dem der Fehler-Breakpoint stammt.  
  
4. Der SDM ruft [IDebugErrorBreakpoint2:: getbreakpointresolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) auf, um den Grund zu erhalten, warum der Fehler Haltepunkt nicht gebunden werden konnte.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
