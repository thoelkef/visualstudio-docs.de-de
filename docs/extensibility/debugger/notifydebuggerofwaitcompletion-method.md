---
title: "NotifyDebuggerOfWaitCompletion-Methode | Microsoft Docs"
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
  - "NotifyDebuggerOfWaitCompletion-Methode, Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# NotifyDebuggerOfWaitCompletion-Methode
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Platzhalter\-Methode, die als haltepunktziel vom Debugger verwendet. Diese Methode darf nicht inline oder optimierten sein.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
## Syntax  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## Hinweise  
 Alle Join\-Vorgänge mit einer Aufgabe sollten diese Methode aufrufen, wenn deren Debugger Benachrichtigung Bit festgelegt ist.  
  
## Anforderungen  
  
## Siehe auch  
 [Task\-Klasse](../../extensibility/debugger/task-class-internal-members.md)