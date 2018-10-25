---
title: Programmieren von Knoten | Microsoft-Dokumentation
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
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdb06d4909bab31169dc0a46156b7e1300b917bc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891335"
---
# <a name="program-nodes"></a>Programmknoten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur eine **Programm Knoten**:  
  
- Ist eine einfache Beschreibung eines Programms.  
  
- Erkennen selbst und den Prozess, den sie in ausgeführt wird, den und angefügt werden kann, um von getrennt, und Beschreiben Sie die Debug-Engine (DE), die sie ggf. erstellt haben.  
  
- Wird durch dargestellt eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle, die in der Regel von einem DE oder Port erstellt. Programmknoten an einen Port hinzugefügt werden, indem [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Wenn ein Programm-Knoten zu einem Port hinzugefügt wird, wird er hinzugefügt, an den Prozess mit dem Programm, das dieses Programm-Knoten darstellt.  
  
  Einige Zeit nach eine Debugsitzung, je nach Implementierung des debugpakets gestartet wird programmknoten dienen zum entsprechenden Programme erstellen. Wenn ein Prozess für seinen Programmen abgefragt wird, werden die Programme aufgelistet, eine für jeden Knoten des Programms.  
  
  Bevor Sie ein Programm angefügt ist, benötigt die IDE nur eine einfache Beschreibung des Programms an. Diese Informationen kann vom Programm Knoten abgerufen werden. Nachdem die Anwendung angefügt ist, muss die IDE Ausführlichere Informationen anzeigen, z. B. eine Liste aller Threads, die in das Programm ausgeführt werden. Diese Informationen werden vom Programm selbst abgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

