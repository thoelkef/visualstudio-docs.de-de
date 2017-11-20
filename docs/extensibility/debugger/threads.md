---
title: Threads | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 150e27c4b8df06784848829bfe713773cf9d48a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="threads"></a>Threads
Im Hinblick auf die Architektur des Debuggers einen **Thread**:  
  
-   Ist die grundlegende Einheit der Berechnung an. Ein Thread ausgeführt wird sequenziell auf die Anweisungen im Kontext einer einzelnen Aufrufliste, wechseln zur nächsten aus einem Kontext aus.  
  
-   Erkennen selbst und das Programm, das er wird ausgeführt, und kann werden mit dem Namen, angehalten und fortgesetzt. Ein Thread kann auch die zugehörigen Stapelrahmen aufzählen und unter bestimmten Umständen kann auf einen anderen Stapelrahmen verschoben werden. Im Rahmen einer Stapelrahmen entspricht kann, ein Thread seine zugeordneten logischen Thread ggf. zurück. Ein Thread verfügt über Eigenschaften, z. B. dem Unterbrechungszähler, die im Fenster Threads von der IDE angezeigt werden können.  
  
-   Dargestellt durch eine [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) Schnittstelle, die in der Regel durch einen Debugging-Modul (DE) oder die virtuelle Maschine als Folge Ausführen eines Programms erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Debuggen des Datenbankmoduls](../../extensibility/debugger/debug-engine.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md)