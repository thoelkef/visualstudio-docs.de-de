---
title: GetTaskSchedulersForDebugger-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4285c9e83521e991deafaf5e35c32acb1dd8867f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839017"
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
 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)