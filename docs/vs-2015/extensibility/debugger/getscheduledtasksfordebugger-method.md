---
title: GetScheduledTasksForDebugger-Methode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4ac6fa753be7672f1e698bda231bd11217c10d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152737"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger-Methode
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Array aller geplanten Tasks ab.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf dieses interne Element vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array aller geplanten Tasks. Jede Aufgabe wird ausgeführt oder die Ausführung ist abgeschlossen.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist nicht Thread sicher und sollte nicht gleichzeitig mit anderen Instanzen von verwendet werden, <xref:System.Threading.Tasks.TaskScheduler> Wenn Sie nur von einem Debugger aufgerufen werden soll, wenn der Debugger alle anderen Threads angehalten hat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)
