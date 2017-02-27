---
title: "SetNotificationForWaitCompletion-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SetNotificationForWaitCompletion-Methode, Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# SetNotificationForWaitCompletion-Methode
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Aktiviert oder deaktiviert das TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION Zustand Bit.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
## Syntax  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### Parameter  
 `enabled`  
  
 `true` Das Bit festgelegt; `false` zu nicht festgelegten Bits.  
  
## Ausnahmen  
  
## Hinweise  
 Der Debugger wird dieses Bit zu Schritt aus einer asynchronen Methodentext. Wenn `enabled` ist `true`, diese Methode muss aufgerufen werden, nur für eine Aufgabe, die noch nicht abgeschlossen wurde. Wenn `enabled` ist `false`, diese Methode kann für abgeschlossene Aufgaben aufgerufen werden. In jedem Fall sollte es nur für Aufgaben Promise\-Stil verwendet werden.  
  
## Anforderungen  
  
## Siehe auch  
 [Task\-Klasse](../../extensibility/debugger/task-class-internal-members.md)