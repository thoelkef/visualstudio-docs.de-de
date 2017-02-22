---
title: "Aufrufen von Debugger-Ereignissen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugereignisse [Debugging-SDK]"
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Aufrufen von Debugger-Ereignissen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ereignisse in Debugsitzungen werden in einer bestimmten Reihenfolge auf.  
  
## Erörterung  
 Um das Muster der Aufrufe zwischen dem Modul \(Debuggen\) und dem DE Debuggen Manager der Sitzung \(SDM\) zu verstehen, stellt Folgendes dar, der aufrufenden Reihenfolge der Ereignisse in einer typischen Debugsitzung auftreten:  
  
1.  [So fügen Sie einem Programm Trennen und Anfügen](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Starten des Debuggers](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Ein Programm beenden](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Erstellen eines Haltepunktes](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Wenn ein Haltepunkt oder Bindung aufgehoben werden](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Haltepunkt von Fehlern](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Wenn Sie einen Haltepunkt schlagen](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Löschen eines Haltepunktes](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Unterbrechungsmodus eingeben](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Im Unterbrechungsmodus befinden](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Ausnahmebehandlung](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## Siehe auch  
 [Erstellen einer benutzerdefinierten Debugmodul](../../extensibility/debugger/creating-a-custom-debug-engine.md)