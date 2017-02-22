---
title: "TaskScheduler-Class - interne Member | Microsoft Docs"
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
  - "TaskScheduler-Klasse [Debugmodule [.NET Framework]"
  - "Debugmodule, TaskScheduler-Klasse [.NET Framework]"
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# TaskScheduler-Class - interne Member
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die internen Member des der <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Klasse, mit denen Sie einen benutzerdefinierten Debugger implementieren. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Threading.Tasks.TaskScheduler> Referenzthema.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diese interne Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## Mitglieder  
  
### Methoden  
  
|Name|Beschreibung|  
|----------|------------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Ruft ein Array aller geplanten Aufgaben.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Ruft ein Array aller <xref:System.Threading.Tasks.TaskScheduler> Objekte, die zurzeit aktiv sind.|  
  
## Hinweise  
  
## Siehe auch  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Parallelen Erweiterung Internals für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)