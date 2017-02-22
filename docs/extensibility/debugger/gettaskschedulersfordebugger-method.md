---
title: "GetTaskSchedulersForDebugger-Methode | Microsoft Docs"
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
  - "GetTaskSchedulersForDebugger-Methode, TaskScheduler-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GetTaskSchedulersForDebugger-Methode
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Array aller <xref:System.Threading.Tasks.TaskScheduler> Objekte, die zurzeit aktiv sind.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## Rückgabewert  
 Ein Array mit allen <xref:System.Threading.Tasks.TaskScheduler> Objekte, die derzeit in dieser <xref:System.AppDomain>.  
  
## Hinweise  
 Diese Methode ist nicht threadsicher und sollte nicht verwendet werden, gleichzeitig mit anderen Instanzen des <xref:System.Threading.Tasks.TaskScheduler>. Es sollte von einem Debugger aufgerufen werden, nur, wenn der Debugger alle anderen Threads angehalten hat.  
  
## Siehe auch  
 [TaskScheduler\-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)