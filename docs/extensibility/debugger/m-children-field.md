---
title: "M_children Feld | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "M_children Feld Klasse ContingentProperties [Debugmodule [.NET Framework]"
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# M_children Feld
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Liste der untergeordneten Aufgaben, die mit dieser Aufgabe registriert sind.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## Hinweise  
 Während der Task ausgeführt wird, sollten nur der Thread, der die Aufgabe ausgeführt wird, dieses Array zugreifen.  
  
 Wenn der Vorgang abgeschlossen ist, können andere Threads dieses Feld zugreifen, solange sie nicht, alles aufheben oder nichts hinzugefügt.  
  
## Siehe auch  
 [ContingentProperties\-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md)