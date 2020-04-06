---
title: Programme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738208"
---
# <a name="programs"></a>Programme
In der Debuggerarchitektur wird ein *Programm*:

- Ein Container für einen Threadsatz und einen Satz von Modulen. Ein Programm hat keine einzige Analogie im Windows-Betriebssystem.

     Ein Programm ist eine Art Unterprozess. Wenn Sie beispielsweise eine Website debuggen, kann ein Skript als Programm betrachtet werden. Während ein Skript im Skriptmodulprozess ausgeführt wird, unabhängig von anderen Skripts, hat es auch einen eigenen Satz von Threads. Ein Debugmodul (DE) wird an ein Programm angefügt und nicht an einen Prozess oder einen Thread.

- Kann sich selbst und den Prozess identifizieren, in dem es ausgeführt wird. Ein Programm kann angefügt werden, von dem es getrennt werden kann, und die DE beschreiben, die es erstellt hat, falls vorhanden. Ein Programm kann auch ausgeführt, angehalten, fortgesetzt und beendet werden.

- Kann alle Threads aufzählen. Ein Programm kann auch einen eigenen Demontagestrom bereitstellen und alle Codekontexte einer bestimmten Dokumentposition aufzählen.

- Wird durch eine [IDebugProgram2-Schnittstelle](../../extensibility/debugger/reference/idebugprogram2.md) dargestellt, die erstellt wurde, bevor das Programm angefügt wird, oder als Teil des Anfügeprozesses, abhängig von der Implementierung. Wenn ein Port die Programme eines Prozesses aufzählt, wird jedes Programm in Übereinstimmung mit einer entsprechenden [IDebugProgramNode2-Schnittstelle](../../extensibility/debugger/reference/idebugprogramnode2.md) erstellt, die als Argument an [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)übergeben wird. Während Debug-Engines `IDebugProgram2` auch Schnittstellen erstellen, um Programme darzustellen, werden diese Programme nicht in Übereinstimmung mit einem Programmknoten erstellt. Die `IDebugProgramNode2` von einem DE erstellten Schnittstellen werden für das eigentliche Debuggen verwendet, während die von einem Port erstellten Schnittstellen nur verwendet werden, um herauszufinden, welche Programme in einem Prozess ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen
- [Prozesse](../../extensibility/debugger/processes.md)
- [Programmknoten](../../extensibility/debugger/program-nodes.md)
- [Module](../../extensibility/debugger/modules.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Dokumentposition](../../extensibility/debugger/document-position.md)
- [Codekontext](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
