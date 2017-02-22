---
title: "IDebugFunctionObject | Microsoft Docs"
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
  - "IDebugFunctionObject"
helpviewer_keywords: 
  - "IDebugFunctionObject-Schnittstelle"
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt eine Funktion dar.  
  
## Syntax  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## Hinweise für Implementierer  
 Ein Ausdrucksauswerter implementiert diese Schnittstelle, um eine Funktion dar.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle ist eine Spezialisierung der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) \-Schnittstelle und wird über [QueryInterface](/visual-cpp/atl/queryinterface) auf die `IDebugObject` Schnittstelle.  
  
## Methoden in Vtable\-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md),  `IDebugFunctionObject` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Erstellt ein Objekt primitiven Datentyps.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Erstellt ein Objekt, das einen Konstruktor verwenden.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Erstellt ein Objekt mit keinen Konstruktor.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Erstellt ein Arrayobjekt.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Erstellt ein String\-Objekt.|  
|[Bewerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Ruft die Funktion und der resultierende Wert als Objekt zurückgegeben.|  
  
## Hinweise  
 Diese Schnittstelle ermöglicht die Auswertung eines Ausdrucks, die Funktionen in eine Analysestruktur darstellen. Die `Create` Methoden in dieser Schnittstelle werden zum Erstellen von Objekten, die die Eingabeparameter für die Methode darstellt. Die Funktion kann dann ausgeführt werden, durch Aufrufen der [Bewerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) \-Methode, die gibt ein Objekt, das den Rückgabewert der Funktion darstellt.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)