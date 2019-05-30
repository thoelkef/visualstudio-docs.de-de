---
title: GetScheduledTasksForDebugger-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49a63462eece9bef09579c7284f72790a3914bc2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353730"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger-Methode
Ruft ein Array aller geplanten Aufgaben.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in *"mscorlib.dll"* )

 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Rückgabewert
 Ein Array aller geplanten Aufgaben. Jede Aufgabe wird ausgeführt oder Ausführung abgeschlossen hat.

## <a name="remarks"></a>Hinweise
 Diese Methode nicht threadsicher ist und Sie sollten nicht gleichzeitig mit anderen Instanzen verwenden <xref:System.Threading.Tasks.TaskScheduler>. Rufen Sie diese Methode von einem Debugger nur, wenn der Debugger alle anderen Threads angehalten hat.

## <a name="see-also"></a>Siehe auch
- [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)