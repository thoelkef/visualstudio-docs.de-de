---
title: "TASK_STATE_CANCELED-Feld | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TASK_STATE_CANCELED Feld Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# TASK_STATE_CANCELED-Feld
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Vorgang wurde abgebrochen, bevor Ausführungsstatus erreichen oder den Abbruch bestätigt und ohne Ausnahme abgeschlossen wurde.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## Hinweise  
 Wenn die [M\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) Feld diesen Wert enthält die <xref:System.Threading.Tasks.Task.Status%2A> \-Eigenschaft gibt <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Siehe auch  
 [Task\-Klasse](../../extensibility/debugger/task-class-internal-members.md)