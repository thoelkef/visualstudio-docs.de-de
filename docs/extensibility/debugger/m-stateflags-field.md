---
title: "M_stateFlags-Feld | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "M_stateFlags-Feld, Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# M_stateFlags-Feld
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Speichert Informationen über den aktuellen Status des der <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## Hinweise  
 In der Regel die <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> \-Eigenschaft auf diesen Wert zugreifen.  
  
 Dieser Member kann eine beliebige Kombination der folgenden Werte sein:  
  
-   [TASK\_STATE\_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK\_STATE\_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK\_STATE\_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK\_STATE\_WAITING\_ON\_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK\_STATE\_RAN\_TO\_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## Siehe auch  
 [Task\-Klasse](../../extensibility/debugger/task-class-internal-members.md)