---
title: "IDebugMemoryBytes2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2"
helpviewer_keywords: 
  - "IDebugMemoryBytes2-Schnittstelle"
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt Bytes des Arbeitsspeichers dar.  
  
## Syntax  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um Bytes im Speicher darzustellen.  
  
## Hinweise für Aufrufer  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) gibt diese Schnittstelle zurück, die Zugriff auf den Systemspeicher zu ermöglichen.  [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) und [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) geben diese Schnittstelle zurück, um den Zugriff auf die Bytes eines Objekts zu ermöglichen.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugMemoryBytes2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Liest eine Folge von Bytes, beginnend an einem bestimmten Speicherort.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Schreibt `dwCount` Bytes beginnend bei `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Ruft die Größe \(in Bytes\) des Arbeitsspeichers ab, der durch diese Schnittstelle dargestellt wird.|  
  
## Hinweise  
 Für Eigenschaften stellt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle, die ein Array darstellt, eine `IDebugMemoryBytes2`\-Schnittstelle, um die Werte in diesem Array zuzugreifen.  
  
 **Arbeitsspeicheransicht** von Visual Studio ruft [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) auf, um eine `IDebugMemoryBytes2`\-Schnittstelle zum Aufrufen des Systemspeichers ab.  Die Adresse, auf das zugegriffen werden soll, wird abgerufen, indem der Ausdruck analysiert, der als Adresse in die Arbeitsspeicher\-Ansicht eingegeben wurde, und dann den analysierten Ausdruck mit [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , um eine `IDebugProperty2`\-Schnittstelle abzurufen ist.  Ein Aufruf von [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) gibt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) zurück, der die Speicheradresse beschreibt.  Dieser Speicher wird anschließend an [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) Lokalisierungskontext und [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)übergeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)