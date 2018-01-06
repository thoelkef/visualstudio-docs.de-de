---
title: Programme | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03b4885e653d879e3aaec1d9a68bc9be144cb676
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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