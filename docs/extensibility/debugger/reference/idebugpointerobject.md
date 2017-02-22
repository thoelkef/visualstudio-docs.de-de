---
title: "IDebugPointerObject | Microsoft Docs"
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
  - "IDebugPointerObject"
helpviewer_keywords: 
  - "IDebugPointerObject-Schnittstelle"
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt ein Mauszeiger\-Objekt.  
  
## Syntax  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## Hinweise für Implementierer  
 Die Auswertung eines Ausdrucks implementiert diese Schnittstelle, um ein Mauszeiger\-Objekt darstellt.  
  
## Hinweise für Aufrufer  
 Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann mithilfe dieser Schnittstelle abrufen [QueryInterface](/visual-cpp/atl/queryinterface) Wenn die `IDebugObject` einen Zeiger darstellt.  
  
## Methoden in Vtable\-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md),  `IDebugPointerObject` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Dereferenzierung](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ruft das Objekt auf die Schnittstelle.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ruft den Wert, den die Schnittstelle als eine Reihe von aufeinander folgenden Bytes verweist.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Legt den Wert, den die Schnittstelle aus einer Reihe von aufeinander folgenden Bytes verweist.|  
  
## Hinweise  
 Eine Auswertung eines Ausdrucks verwendet diese Schnittstelle, um einen Zeiger in eine Analysestruktur darzustellen.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)