---
title: Programme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3d1c1e72524c393fdb3adc4477ea9ae374fbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="programs"></a>Programs
Im Hinblick auf die Architektur des Debuggers einen **Programm**:  
  
-   Ist ein Container für eine Gruppe von Threads und einen Satz von Modulen. Ein Programm hat keine einzelnen Analogie in Windows-Betriebssystems.  
  
     Ein Programm ist eine Art von Unterprozess. Während des Debuggens einer Websites kann beispielsweise ein Skript als Programm betrachtet werden. Während ein Skript in den Skriptprozess-Modul ausgeführt wird, unabhängig von anderen Skripts besitzt auch über einen eigenen Satz von Threads. Ein Debugging-Modul (DE) wird an ein Programm, und nicht auf einen Prozess oder einen Thread angefügt.  
  
-   Erkennen selbst und den Prozess, den es im ausgeführt wird, den und von getrennt, und beschreiben, die sie ggf. erstellt DE angefügt werden kann. Ein Programm kann ausführen, beenden, den Vorgang fortzusetzen, und beendet werden.  
  
-   Alle Threads können aufgelistet werden. Ein Programm kann auch einen eigenen Disassembly Stream bereitgestellt und kann die Code Kontexten von einem angegebenen Dokumentposition aufzählen.  
  
-   Wird durch dargestellt ein [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, bevor die Anwendung angefügt ist, oder als Teil der anfügungsvorgang, je nach Implementierung erstellt. Wenn ein Port die Programmen eines Prozesses aufgezählt wird, wird jedes Programm in Übereinstimmung mit einer entsprechenden erstellt [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle übergeben, als Argument an [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Während Debugmodule auch erstellen `IDebugProgram2` Schnittstellen zum Darstellen von Programmen, die diese Programme werden nicht in Übereinstimmung mit einem Programm Knoten erstellt. Die `IDebugProgramNode2` Schnittstellen, die von einer bereitgestellten Kompatibilitätsrichtlinie erstellt dienen zum tatsächlichen Debuggen, während solche, die von einem Port erstellt verwendet werden, nur für die Ermittlung, welche Programme in einem Prozess ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Programm-Knoten](../../extensibility/debugger/program-nodes.md)   
 [Module](../../extensibility/debugger/modules.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debuggen des Datenbankmoduls](../../extensibility/debugger/debug-engine.md)   
 [Dokumentposition](../../extensibility/debugger/document-position.md)   
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)