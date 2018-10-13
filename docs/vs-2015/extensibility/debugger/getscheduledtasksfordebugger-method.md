---
title: GetScheduledTasksForDebugger-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57d71dff0404b8bcea7f7274b943925eb45e0830
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201974"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger-Methode
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Array aller geplanten Aufgaben.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array aller geplanten Aufgaben. Jede Aufgabe wird ausgeführt oder Ausführung abgeschlossen hat.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist nicht threadsicher und sollte nicht verwendet werden, gleichzeitig mit anderen Instanzen der <xref:System.Threading.Tasks.TaskScheduler> sollte aufgerufen werden von einem Debugger nur, wenn der Debugger alle anderen Threads angehalten hat.  
  
## <a name="see-also"></a>Siehe auch  
 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)

