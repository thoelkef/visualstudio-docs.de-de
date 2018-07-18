---
title: GetTaskSchedulersForDebugger Methode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5d0b78a4f115d1ba07848db914289c35034d465
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099310"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger-Methode
Ruft ein Array aller <xref:System.Threading.Tasks.TaskScheduler> Objekte, die derzeit aktiv sind.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da dieses interne Member von .NET Framework zugegriffen werden kann, wird die folgende Syntax gemeinsame Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array aller <xref:System.Threading.Tasks.TaskScheduler> Objekte, die in diesem derzeit aktiv sind <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist nicht threadsicher und sollte nicht verwendet werden, gleichzeitig mit anderen Instanzen von <xref:System.Threading.Tasks.TaskScheduler>. Es sollte von einem Debugger aufgerufen werden, nur, wenn der Debugger alle anderen Threads angehalten hat.  
  
## <a name="see-also"></a>Siehe auch  
 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)