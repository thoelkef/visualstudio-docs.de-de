---
title: Löschen eines Haltepunkts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409411"
---
# <a name="deleting-a-breakpoint"></a>Löschen eines Haltepunkts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden beschreibt den Prozess, wenn einen ausstehenden Haltepunkt zu löschen:  
  
## <a name="deletion-process"></a>Vorgang zum Löschen  
 Ruft die Sitzungs-Debug-Manager (SDM) die [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) Methode, um den ausstehenden Haltepunkt, und alle gebundener Haltepunkte entfernen daraus gebunden.  
  
> [!NOTE]
> Ein einzelnen gebundener Haltepunkt auch gelöscht werden, durch einen Aufruf von [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
