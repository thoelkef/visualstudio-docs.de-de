---
title: "Erstellen eines Haltepunkts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Haltepunkte, erstellen"
  - "Debuggen [Debugging-SDK], Erstellen von Haltepunkten"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Erstellen eines Haltepunkts
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden beschreibt den Vorgang des Erstellens eines Haltepunkts.  
  
## Methoden in der Breakpoint\-Erstellung  
 Wenn das Modul benötigt wird, um einen Haltepunkt zu binden, geladen wird, ruft der Debug\- Manager der Sitzung \(SDM\) die folgenden Methoden auf:  
  
1.  [IDebugPendingBreakpoint2::Aktivieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2::Virtualisieren Sie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  **CanBind** wird nur aufgerufen, wenn ein Benutzer einen Haltepunkt im Fenster Haltepunkte ausführt.  
  
4.  [IDebugPendingBreakpoint2::Bindung](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)