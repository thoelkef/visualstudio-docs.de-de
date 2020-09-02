---
title: Programme | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9070b33c7522cdc13fd6217956fcab72cd83f8d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153646"
---
# <a name="programs"></a>Programme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ist ein **Programm**:  
  
- Ist ein Container für einen Satz von Threads und einen Satz von Modulen. Ein Programm hat im Windows-Betriebssystem keine einzige Analogie.  
  
     Ein Programm ist eine Art von unter Prozessen. Wenn Sie z. b. eine Website Debuggen, kann ein Skript als Programm angesehen werden. Während ein Skript im Skript-Engine-Prozess unabhängig von anderen Skripts ausgeführt wird, verfügt es auch über einen eigenen Satz von Threads. Eine Debug-Engine (de) wird an ein Programm angefügt, nicht an einen Prozess oder einen Thread.  
  
- Identifiziert sich selbst und den Prozess, in dem er ausgeführt wird, und kann an ihn angefügt werden, von ihm getrennt werden und den von ihm erstellten Dienst beschreiben, sofern vorhanden. Ein Programm kann ausgeführt, beendet, fortgesetzt und beendet werden.  
  
- Kann alle zugehörigen Threads auflisten. Ein Programm kann auch seinen eigenen disassemblystream bereitstellen und alle Code Kontexte einer bestimmten Dokument Position auflisten.  
  
- Wird durch eine [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle dargestellt, die erstellt wird, bevor das Programm angefügt wird, oder als Teil des Anfüge Prozesses, abhängig von der Implementierung. Wenn ein Port die Programme eines Prozesses auflistet, wird jedes Programm in Übereinstimmung mit einer entsprechenden [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle erstellt, die als Argument an [addprogram Node](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)weitergeleitet wird. Obwohl debugengines auch `IDebugProgram2` Schnittstellen zur Darstellung von Programmen erstellen, werden diese Programme nicht in Übereinstimmung mit einem Programmknoten erstellt. Die `IDebugProgramNode2` von einem de erstellten Schnittstellen werden für das eigentliche Debuggen verwendet, während die von einem Port erstellten Schnittstellen nur für die Ermittlung der Programme verwendet werden, die in einem Prozess ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Programmknoten](../../extensibility/debugger/program-nodes.md)   
 [Modulen](../../extensibility/debugger/modules.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Dokument Position](../../extensibility/debugger/document-position.md)   
 [Code Kontext](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
