---
title: Programmknoten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153656"
---
# <a name="program-nodes"></a>Programmknoten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ein **Programmknoten**:  
  
- Ist eine vereinfachte Beschreibung eines Programms.  
  
- Identifiziert sich selbst und den Prozess, in dem Sie ausgeführt wird, und kann an Sie angehängt, von getrennt werden und die Debug-Engine (de) beschreiben, von der Sie erstellt wurde (sofern vorhanden).  
  
- Wird durch eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle dargestellt, die in der Regel durch eine de oder einen Port erstellt wird. Programmknoten werden einem Port durch Aufrufen von [addprogramnode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)hinzugefügt. Wenn ein Programmknoten einem Port hinzugefügt wird, wird er dem Prozess hinzugefügt, der das Programm enthält, das dieser Programmknoten darstellt.  
  
  Wenn eine Debugsitzung gestartet wird, werden in Abhängigkeit von der Implementierung des debugpakets Programmknoten verwendet, um entsprechende Programme zu erstellen. Wenn ein Prozess für seine Programme abgefragt wird, werden die Programme aufgelistet, eine für jeden Programmknoten.  
  
  Bevor ein Programm an angefügt wird, benötigt die IDE nur eine vereinfachte Beschreibung des Programms. Diese Informationen können vom Programmknoten abgerufen werden. Nachdem das Programm an angefügt wurde, muss die IDE ausführlichere Informationen anzeigen, z. b. eine Liste aller im Programm ausgelaufenden Threads. Diese Informationen werden vom Programm selbst abgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programme](../../extensibility/debugger/programs.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
