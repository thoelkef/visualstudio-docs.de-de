---
title: "IDebugBinder3 | Microsoft Docs"
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
  - "IDebugBinder3"
helpviewer_keywords: 
  - "IDebugBinder3-Schnittstelle"
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle ermöglicht den Zugriff auf Typen, Aliase und benutzerdefinierte Schnellansicht Diensten.  
  
## Syntax  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## Hinweise für Implementierer  
 Ein Debugmodul implementiert diese Schnittstelle, um Aliase, benutzerdefinierte Schnellansicht Diensten und den Zugriff auf Objekttypen.  
  
## Hinweise für Aufrufer  
 Eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle ruft diese Schnittstelle mit [QueryInterface](/visual-cpp/atl/queryinterface).  
  
## Methoden in Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden von der [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) \-Schnittstelle, diese Schnittstelle implementiert die folgenden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Ruft ein Speicherobjekt, das den Speicher, den dieses Objekt gebunden ist, darstellt.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Ruft die Ausnahme, die diesem Objekt \(falls vorhanden\) zugeordnet,|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Ruft einen Alias mit dem angegebenen Namen ab,|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Ruft ein Array aller Aliase für dieses Objekt ab,|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Ruft die Anzahl der diesem Objekt zugeordneten Argumenttypen,|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Ruft eine Liste der Argumenttypen, die diesem Objekt zugeordnet,|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Ruft eine Schnittstelle für eine schnellansichtsdienst,|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Konvertiert ein Objektspeicherort oder eine 64\-Bit\-Speicheradresse auf einen Speicherkontext.|  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)