---
title: Programmknoten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738218"
---
# <a name="program-nodes"></a>Programmknoten
In der Debuggerarchitektur wird ein *Programmknoten*:

- Ist eine leichte Beschreibung eines Programms.

- Kann sich selbst und den Prozess identifizieren, in dem es ausgeführt wird. Ein Programmknoten kann angefügt werden, von dem er getrennt werden kann, und das Debugmodul (DE) beschreiben, das ihn erstellt hat.

- Wird durch eine [IDebugProgramNode2-Schnittstelle](../../extensibility/debugger/reference/idebugprogramnode2.md) dargestellt, die in der Regel von einem DE oder Port erstellt wird. Programmknoten werden einem Port durch Aufrufen von [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)hinzugefügt. Wenn ein Programmknoten zu einem Port hinzugefügt wird, wird er dem Prozess hinzugefügt, der das Programm enthält, das dieser Programmknoten darstellt.

  Je nach Dem Start einer Debugsitzung werden je nach Implementierung des Debugpakets Programmknoten verwendet, um entsprechende Programme zu erstellen. Wenn ein Prozess für seine Programme abgefragt wird, werden die Programme aufgezählt, eines für jeden Programmknoten.

  Bevor ein Programm angefügt wird, benötigt die IDE nur eine einfache Beschreibung des Programms. Diese Informationen können vom Programmknoten abgerufen werden. Sobald das Programm angefügt ist, zeigt die IDE detailliertere Informationen an, z. B. eine Liste aller Threads, die im Programm ausgeführt werden. Diese Informationen werden aus dem Programm selbst abgerufen.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Prozesse](../../extensibility/debugger/processes.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
