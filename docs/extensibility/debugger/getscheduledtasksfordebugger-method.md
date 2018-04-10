---
title: GetScheduledTasksForDebugger Methode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1c27bd57684fc0a4de0bf56bcc8db9a5561f7d1f
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger-Methode
Ruft ein Array aller geplanten Aufgaben ab.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da dieses interne Member von .NET Framework zugegriffen werden kann, wird die folgende Syntax gemeinsame Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array von aller geplanten Aufgaben. Jede Aufgabe wird ausgeführt oder hat die Ausführung beendet.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist nicht threadsicher und sollte nicht verwendet werden, gleichzeitig mit anderen Instanzen von <xref:System.Threading.Tasks.TaskScheduler> sollte aufgerufen werden von einem Debugger nur, wenn der Debugger alle anderen Threads angehalten hat.  
  
## <a name="see-also"></a>Siehe auch  
 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)