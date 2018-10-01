---
title: Haltepunktfehler | Microsoft-Dokumentation
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
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 656f96a344e3d527407cd5a91b0a5910e1e6005c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512999"
---
# <a name="breakpoint-errors"></a>Haltepunktfehler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Haltepunktfehler](https://docs.microsoft.com/visualstudio/extensibility/debugger/breakpoint-errors).  
  
Die folgenden beschreibt den Prozess aus, wenn ein Haltepunkt zum Binden an Code versucht jedoch ein Fehler auftritt:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Problembehandlung bei einem Breakpoint-Fehler  
  
1.  Die Debug-Engine (DE) sendet ein [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) für die Sitzung Debug-Manager (SDM).  
  
2.  Die SDM-Aufrufe [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) um den Haltepunkt Fehler zu erhalten.  
  
3.  Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) abzurufenden den ausstehenden Haltepunkt, von dem der Haltepunkt Fehler verursacht wurde.  
  
4.  Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) abzurufenden den Grund, warum der Haltepunkt Fehler beim Binden Fehler.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)

