---
title: "AsyncTaskMethodBuilder &lt; TResult &gt; Struktur - interne Member | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "AsyncTaskMethodBuilder < TResult > Struktur [Debugmodule [.NET Framework]"
  - "Debugmodule, AsyncTaskMethodBuilder < TResult >-Struktur [.NET Framework]"
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# AsyncTaskMethodBuilder &lt; TResult &gt; Struktur - interne Member
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Referenzthema.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diese interne Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Interne Member  
  
|Name|Beschreibung|  
|----------|------------------|  
|[ObjectIdForDebugger\-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|  
|[M\_task\-Feld](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Stellt die verzögert initialisierte Aufgabe erstellt.|  
  
## Siehe auch  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Parallelen Erweiterung Internals für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)