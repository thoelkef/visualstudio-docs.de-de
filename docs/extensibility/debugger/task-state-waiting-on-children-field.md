---
title: TASK_STATE_WAITING_ON_CHILDREN Feld | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27b9963db54d939b3d509da451478c20dbe0e7d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712584"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN Feld
Die Aufgabe hat die Ausführung des Delegaten abgeschlossen und wartet implizit darauf, dass angefügte untergeordnete Aufgaben abgeschlossen sind.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

 Da Sie über .NET Framework nicht auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Bemerkungen
 Wenn das [Feld m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) diesen <xref:System.Threading.Tasks.Task.Status%2A> Wert <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>enthält, gibt die Eigenschaft zurück.

## <a name="see-also"></a>Weitere Informationen
- [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
