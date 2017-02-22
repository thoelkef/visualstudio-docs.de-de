---
title: "AsyncVoidMethodBuilder-Struktur - interne Member | Microsoft Docs"
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
  - "Debugmodule, AsyncVoidMethodBuilder-Struktur [.NET Framework]"
  - "AsyncVoidMethodBuilder-Struktur [Debugmodule [.NET Framework]"
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# AsyncVoidMethodBuilder-Struktur - interne Member
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Referenzthema.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diese interne Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Interne Member  
  
|Name|Beschreibung|  
|----------|------------------|  
|[ObjectIdForDebugger\-Eigenschaft](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|  
|[M\_objectIdForDebugger\-Feld](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Stellt das verzögert initialisierte Objekt, das vom Debugger zur eindeutigen Identifizierung von diesem Generator verwendet.|  
  
## Siehe auch  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Parallelen Erweiterung Internals für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)