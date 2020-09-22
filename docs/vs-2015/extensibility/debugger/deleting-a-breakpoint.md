---
title: Löschen eines Breakpoints | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841062"
---
# <a name="deleting-a-breakpoint"></a>Löschen eines Haltepunkts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird der Prozess zum Löschen eines ausstehenden Breakpoints beschrieben:  
  
## <a name="deletion-process"></a>Löschvorgang  
 Der Session Debug Manager (SDM) Ruft die [IDebugPendingBreakpoint2::D Elete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) -Methode auf, um den ausstehenden Haltepunkt und alle von ihm gebundenen gebundenen Haltepunkte zu entfernen.  
  
> [!NOTE]
> Ein einzelner gebundener Haltepunkt kann auch durch einen [IDebugBoundBreakpoint2::D Elete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)-aufrufungspunkt gelöscht werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
