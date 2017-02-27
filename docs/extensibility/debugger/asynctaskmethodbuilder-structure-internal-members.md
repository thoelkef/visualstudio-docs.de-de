---
title: "AsyncTaskMethodBuilder-Struktur - interne Member | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, AsyncTaskMethodBuilder-Struktur [.NET Framework]"
  - "AsyncTaskMethodBuilder-Struktur [Debugmodule [.NET Framework]"
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# AsyncTaskMethodBuilder-Struktur - interne Member
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Referenzthema.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diese interne Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Interne Member  
  
|Name|Beschreibung|  
|----------|------------------|  
|[ObjectIdForDebugger\-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|  
|[M\_builder\-Feld](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Das generische Generatorobjekt, das diese Instanz nicht generische Delegaten, darstellt.|  
  
## Siehe auch  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Parallelen Erweiterung Internals für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)