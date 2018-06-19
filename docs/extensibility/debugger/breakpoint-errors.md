---
title: Haltepunkt-Fehler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e3c7271cc573388231045143f275d1032bef437
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099882"
---
# <a name="breakpoint-errors"></a>Haltepunkt-Fehler
Die folgenden beschreibt den Prozess aus, wenn ein Haltepunkt an Code binden möchte jedoch ein Fehler auftritt:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Problembehandlung bei einem Breakpoint-Fehler  
  
1.  Die Debugging-Modul (DE) sendet eine [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) auf der Sitzungs-Manager (SDM).  
  
2.  Ruft die SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) um den Haltepunkt Fehler abzurufen.  
  
3.  Ruft die SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) abzurufenden ausstehenden Haltepunkt, von dem der Fehler Breakpoint stammt.  
  
4.  Ruft die SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) abzurufenden den Grund, warum der Fehler Breakpoint Fehler bei der Bindung.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)