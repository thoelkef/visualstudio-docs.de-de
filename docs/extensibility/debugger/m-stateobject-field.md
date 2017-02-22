---
title: "M_stateObject Feld | Microsoft Docs"
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
  - "M_stateObject Feld Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# M_stateObject Feld
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Objekt, das Daten darstellt, die die Aktion verwendet wird.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.field assembly object m_stateObject  
```  
  
## Hinweise  
 Dies ist der `state` \-Parameter in der <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor. Es ist auch das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Eigenschaft.  
  
## Siehe auch  
 [Task\-Klasse](../../extensibility/debugger/task-class-internal-members.md)