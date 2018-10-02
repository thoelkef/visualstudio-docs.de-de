---
title: Programme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c6db9d45f9bb421738b71e630482cbbb8f6525c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524725"
---
# <a name="programs"></a>Programs
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Programme](https://docs.microsoft.com/visualstudio/extensibility/debugger/programs).  
  
Im Hinblick auf die Debugger-Architektur eine **Programm**:  
  
-   Ist ein Container für eine Reihe von Threads und einem Satz von Modulen. Ein Programm hat keine einzelne Analogie in das Windows-Betriebssystem.  
  
     Ein Programm ist eine Art von Unterprozess. Wenn Sie eine Website Debuggen, kann z. B. ein Skript als Programm angezeigt werden. Wenn ein Skript im Skript-Engine-Prozess ausgeführt wird, verfügt über unabhängig von anderen Skripts, es auch einen eigenen Satz von Threads. Fügt an eine Debug-Engine (DE) an ein Programm und nicht für einen Prozess oder einen Thread.  
  
-   Erkennen selbst und den Prozess, den sie in ausgeführt wird, den und angefügt werden kann, um von getrennt, und Beschreiben Sie die DE, die sie ggf. erstellt haben. Ein Programm kann ausgeführt, beenden und den Vorgang fortzusetzen, und beendet werden.  
  
-   Können alle Threads auflisten. Ein Programm kann auch einen eigenen Stream erhält Disassembly angeben und kann die Codekontexte einer angegebenen Dokument Position auflisten.  
  
-   Wird durch dargestellt eine [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, bevor das Programm angefügt ist, oder als Teil der anfügungsprozess, je nach Implementierung erstellt. Wenn Sie ein Port eines Prozesses Programme aufgezählt wird, wird jedes Programm in Übereinstimmung mit einer entsprechenden erstellt [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle zu übergeben, als Argument an [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Während der Debug-Engines auch erstellen `IDebugProgram2` Schnittstellen zum Darstellen der Programme, die diese Programme werden nicht in Übereinstimmung mit einem Programm-Knoten erstellt. Die `IDebugProgramNode2` Schnittstellen, die von einer bereitgestellten Kompatibilitätsrichtlinie erstellt werden zum tatsächlichen zu debuggen, während denen durch einen Port verwendet werden, nur für die Ermittlung, welche Programme in einem Prozess ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Programmknoten](../../extensibility/debugger/program-nodes.md)   
 [Module](../../extensibility/debugger/modules.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Dokumentposition](../../extensibility/debugger/document-position.md)   
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

