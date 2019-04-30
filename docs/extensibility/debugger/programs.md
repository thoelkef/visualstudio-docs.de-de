---
title: Programme | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd38fa74d43842bcb1a08c682049b9998bc11ab3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889085"
---
# <a name="programs"></a>Programs
Architektur der Debugger eine *Programm*:

- Ist ein Container für eine Reihe von Threads und einem Satz von Modulen. Ein Programm hat keine einzelne Analogie in das Windows-Betriebssystem.

     Ein Programm ist eine Art von Unterprozess. Wenn Sie eine Website Debuggen, kann z. B. ein Skript als Programm angezeigt werden. Wenn ein Skript im Skript-Engine-Prozess ausgeführt wird, verfügt über unabhängig von anderen Skripts, es auch einen eigenen Satz von Threads. Fügt an eine Debug-Engine (DE) an ein Programm und nicht für einen Prozess oder einen Thread.

- Erkennen sich selbst und den Prozess, den er ausgeführt wird. Ein Programm kann von getrennt, und beschreiben die DE, die sie erstellt haben, wenn alle angefügt werden. Ein Programm kann auch ausführen, beenden, fortsetzen und werden beendet.

- Können alle Threads auflisten. Ein Programm kann auch einen eigenen Stream erhält Disassembly angeben und kann die Codekontexte einer angegebenen Dokument Position auflisten.

- Wird durch dargestellt eine [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, bevor das Programm angefügt ist, oder als Teil der anfügungsprozess, je nach Implementierung erstellt. Wenn Sie ein Port eines Prozesses Programme aufgezählt wird, wird jedes Programm in Übereinstimmung mit einer entsprechenden erstellt [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle zu übergeben, als Argument an [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Während der Debug-Engines auch erstellen `IDebugProgram2` Schnittstellen zum Darstellen der Programme, die diese Programme werden nicht in Übereinstimmung mit einem Programm-Knoten erstellt. Die `IDebugProgramNode2` Schnittstellen, die von einer bereitgestellten Kompatibilitätsrichtlinie erstellt werden zum tatsächlichen zu debuggen, während denen durch einen Port verwendet werden, nur für die Ermittlung, welche Programme in einem Prozess ausgeführt werden.

## <a name="see-also"></a>Siehe auch
- [Prozesse](../../extensibility/debugger/processes.md)
- [Programmknoten](../../extensibility/debugger/program-nodes.md)
- [Module](../../extensibility/debugger/modules.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-engine](../../extensibility/debugger/debug-engine.md)
- [Dokumentposition](../../extensibility/debugger/document-position.md)
- [Codekontext](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)