---
title: GetTaskSchedulersForDebugger-Methode | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738649"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger-Methode
Ruft ein Array <xref:System.Threading.Tasks.TaskScheduler> aller Objekte ab, die derzeit aktiv sind.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

 Da Sie über .NET Framework nicht auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Rückgabewert
 Ein Array <xref:System.Threading.Tasks.TaskScheduler> aller Objekte, die <xref:System.AppDomain>derzeit in dieser aktiv sind.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht threadsicher und Sie sollten sie <xref:System.Threading.Tasks.TaskScheduler>nicht gleichzeitig mit anderen Instanzen von verwenden. Rufen Sie diese Methode nur von einem Debugger auf, wenn der Debugger alle anderen Threads angehalten hat.

## <a name="see-also"></a>Weitere Informationen
- [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)
