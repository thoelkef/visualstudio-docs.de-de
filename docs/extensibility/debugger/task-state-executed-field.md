---
title: "TASK_STATE_EXECUTED-Feld | Microsoft Docs"
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
  - "TASK_STATE_EXECUTED Feld Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# TASK_STATE_EXECUTED-Feld
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Aufgabe wird ausgeführt, wurde aber noch nicht abgeschlossen.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## Hinweise  
 Wenn die [M\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) Feld diesen Wert enthält die <xref:System.Threading.Tasks.Task.Status%2A> \-Eigenschaft gibt <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Siehe auch  
 [Task\-Klasse](../../extensibility/debugger/task-class-internal-members.md)