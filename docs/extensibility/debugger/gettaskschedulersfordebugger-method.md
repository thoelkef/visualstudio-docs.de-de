---
title: Gettaskschedulersfordebugger-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738649"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger-Methode
Ruft ein Array aller- <xref:System.Threading.Tasks.TaskScheduler> Objekte ab, die derzeit aktiv sind.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Da Sie nicht über das .NET Framework auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Rückgabewert
 Ein Array aller- <xref:System.Threading.Tasks.TaskScheduler> Objekte, die zurzeit in diesem aktiv sind <xref:System.AppDomain> .

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht Thread sicher und sollte nicht gleichzeitig mit anderen Instanzen von verwendet werden <xref:System.Threading.Tasks.TaskScheduler> . Diese Methode wird nur von einem Debugger aufgerufen, wenn der Debugger alle anderen Threads angehalten hat.

## <a name="see-also"></a>Weitere Informationen
- [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)
