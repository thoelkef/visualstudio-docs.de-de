---
title: "TASK_STATE_WAITING_ON_CHILDREN-Feld | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TASK_STATE_WAITING_ON_CHILDREN Feld Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TASK_STATE_WAITING_ON_CHILDREN-Feld
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Aufgabe hat die Ausführung seines Delegaten beendet und wartet implizit angefügte untergeordnete Aufgaben abgeschlossen.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## Hinweise  
 Wenn die [M\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) Feld diesen Wert enthält die <xref:System.Threading.Tasks.Task.Status%2A> \-Eigenschaft gibt <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Siehe auch  
 [Task\-Klasse](../../extensibility/debugger/task-class-internal-members.md)