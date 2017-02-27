---
title: "ContingentProperties Class - interne Member | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ContingentProperties-Klasse [Debugmodule [.NET Framework]"
  - "Debugmodule, ContingentProperties-Klasse [.NET Framework]"
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# ContingentProperties Class - interne Member
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enthält zusätzliche Eigenschaften für ein <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diese interne Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## Mitglieder  
  
### Felder  
  
|Name|Beschreibung|  
|----------|------------------|  
|[m\_children](../../extensibility/debugger/m-children-field.md)|Die Liste der untergeordneten Aufgaben, die mit dieser Aufgabe registriert sind.|  
  
## Hinweise  
 .NET Framework initialisiert die Felder dieser Klasse nur, wenn sie benötigt werden.  
  
## Siehe auch  
 [Parallelen Erweiterung Internals für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)