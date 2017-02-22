---
title: "GetScheduledTasksForDebugger-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetScheduledTasksForDebugger Methode TaskScheduler-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GetScheduledTasksForDebugger-Methode
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Array aller geplanten Aufgaben.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## Rückgabewert  
 Ein Array aller geplanten Aufgaben. Jede Aufgabe wird ausgeführt oder die Ausführung abgeschlossen ist.  
  
## Hinweise  
 Diese Methode ist nicht threadsicher und sollte nicht verwendet werden, gleichzeitig mit anderen Instanzen der <xref:System.Threading.Tasks.TaskScheduler> sollte aufgerufen werden von einem Debugger nur, wenn der Debugger alle anderen Threads angehalten hat.  
  
## Siehe auch  
 [TaskScheduler\-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)