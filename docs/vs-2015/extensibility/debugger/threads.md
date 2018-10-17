---
title: Threads | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bda2bc0c79f766b4c6322850a22d2a830499ff58
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188267"
---
# <a name="threads"></a>Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur eine **Thread**:  
  
-   Ist die grundlegende Einheit für die Berechnung an. Ein Thread führt nacheinander die Anweisungen innerhalb des Kontexts von einer einzigen Aufrufliste, die aus einem Codekontext mit dem nächsten fortgefahren.  
  
-   Erkennen sich selbst und das Programm ausgeführt wird, und können werden mit dem Namen, angehalten und fortgesetzt. Ein Thread kann auch der zugeordnete Stapelrahmen aufzählen und unter bestimmten Umständen kann in einen anderen Stapelrahmen verschoben werden. Im Rahmen einen Stapelrahmen kann, ein Thread seine zugeordneten logischen Thread auf, ggf. zurück. Ein Thread verfügt über Eigenschaften, z. B. dem Unterbrechungszähler, die im Fenster "Threads" der IDE angezeigt werden können.  
  
-   Wird durch dargestellt eine [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) Schnittstelle, die in der Regel von einer Debug-Engine (DE) oder die virtuelle Maschine, daher das Ausführen eines Programms erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md)

