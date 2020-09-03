---
title: GetScheduledTasksForDebugger-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738666"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger-Methode
Ruft ein Array aller geplanten Tasks ab.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Rückgabewert
 Ein Array aller geplanten Tasks. Jede Aufgabe wird ausgeführt oder die Ausführung ist abgeschlossen.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht Thread sicher und sollte nicht gleichzeitig mit anderen Instanzen von verwendet werden <xref:System.Threading.Tasks.TaskScheduler> . Diese Methode wird nur von einem Debugger aufgerufen, wenn der Debugger alle anderen Threads angehalten hat.

## <a name="see-also"></a>Weitere Informationen
- [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)
