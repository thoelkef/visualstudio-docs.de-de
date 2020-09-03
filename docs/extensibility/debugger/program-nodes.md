---
title: Programmknoten | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738218"
---
# <a name="program-nodes"></a>Programmknoten
In der Debugger-Architektur ein *Programmknoten*:

- Ist eine vereinfachte Beschreibung eines Programms.

- Kann sich selbst und den Prozess identifizieren, in dem er ausgeführt wird. Ein Programmknoten kann angefügt werden, von getrennt werden und die Debug-Engine (de) beschreiben, von der er erstellt wurde (sofern vorhanden).

- Wird durch eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle dargestellt, die in der Regel durch eine de oder einen Port erstellt wird. Programmknoten werden einem Port durch Aufrufen von [addprogramnode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)hinzugefügt. Wenn ein Programmknoten einem Port hinzugefügt wird, wird er dem Prozess hinzugefügt, der das Programm enthält, das dieser Programmknoten darstellt.

  Wenn eine Debugsitzung gestartet wird, werden in Abhängigkeit von der Implementierung des debugpakets Programmknoten verwendet, um entsprechende Programme zu erstellen. Wenn ein Prozess für seine Programme abgefragt wird, werden die Programme aufgelistet, eine für jeden Programmknoten.

  Bevor ein Programm an angefügt wird, benötigt die IDE nur eine vereinfachte Beschreibung des Programms. Diese Informationen können vom Programmknoten abgerufen werden. Wenn das Programm an angefügt ist, zeigt die IDE ausführlichere Informationen an, z. b. eine Liste aller Threads, die im Programm ausgeführt werden. Diese Informationen werden vom Programm selbst abgerufen.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Prozesse](../../extensibility/debugger/processes.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
