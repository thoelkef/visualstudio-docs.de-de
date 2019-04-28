---
title: GetTaskSchedulersForDebugger-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5df6dc3147a92f14d6858a82a6d997442dec30b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925653"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger-Methode
Ruft ein Array aller <xref:System.Threading.Tasks.TaskScheduler> Objekte, die zurzeit aktiv sind.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)

 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Rückgabewert
 Ein Array aller <xref:System.Threading.Tasks.TaskScheduler> Objekte, die in diesem zurzeit aktiv sind <xref:System.AppDomain>.

## <a name="remarks"></a>Hinweise
 Diese Methode nicht threadsicher ist und Sie sollten nicht gleichzeitig mit anderen Instanzen verwenden <xref:System.Threading.Tasks.TaskScheduler>. Rufen Sie diese Methode von einem Debugger nur, wenn der Debugger alle anderen Threads angehalten hat.

## <a name="see-also"></a>Siehe auch
- [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)