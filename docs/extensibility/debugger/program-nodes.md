---
title: Programmieren von Knoten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc87a24b35993f200c709ee033fffe6a4ecb120
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903620"
---
# <a name="program-nodes"></a>Programmknoten
Architektur der Debugger eine *Programm Knoten*:  
  
- Ist eine einfache Beschreibung eines Programms.  
  
- Erkennen sich selbst und den Prozess, den er ausgeführt wird. Ein Programm-Knoten kann von getrennt, und beschreiben die Debug-Engine (DE), die sie erstellt haben, wenn alle angefügt werden.  
  
- Wird durch dargestellt eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle, die in der Regel von einem DE oder Port erstellt. Programmknoten an einen Port hinzugefügt werden, indem [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Wenn ein Programm-Knoten zu einem Port hinzugefügt wird, wird er hinzugefügt, an den Prozess mit dem Programm, das dieses Programm-Knoten darstellt.  
  
  Einige Zeit nach eine Debugsitzung, je nach Implementierung des debugpakets gestartet wird programmknoten dienen zum entsprechenden Programme erstellen. Wenn ein Prozess für seinen Programmen abgefragt wird, werden die Programme aufgelistet, eine für jeden Knoten des Programms.  
  
  Bevor Sie ein Programm angefügt ist, benötigt die IDE nur eine einfache Beschreibung des Programms an. Diese Informationen kann vom Programm Knoten abgerufen werden. Sobald die Anwendung angefügt ist, zeigt die IDE Weitere ausführliche Informationen, z. B. eine Liste aller Threads im Programm ausgeführt wird. Diese Informationen werden vom Programm selbst abgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debug-engine](../../extensibility/debugger/debug-engine.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)