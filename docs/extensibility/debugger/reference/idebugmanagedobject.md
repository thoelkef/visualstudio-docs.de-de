---
title: "IDebugManagedObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject-Schnittstelle"
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle ermöglicht die Auswertung eines Ausdrucks \(EE\) zum Aufrufen von Eigenschaften oder Methoden auf Instanzen Wert \(z. B. `System.Decimal`\) und ihren Wert ohne Aufruf festlegen [Bewerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) auf die Anwendung gedebuggt wird.  
  
## Syntax  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## Hinweise für Implementierer  
 Ein Ausdrucksauswerter implementiert diese Schnittstelle, um eine verwaltete Codeobjekt, z. B. eine Variable darstellen.  
  
## Hinweise für Aufrufer  
 Um diese Schnittstelle zu erhalten, rufen Sie [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) auf eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) die eine Instanz einer Klasse Wert darstellt.  
  
## Methoden in Vtable\-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md),  `IDebugManagedObject` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Gibt eine Schnittstelle, die das verwaltete Codeobjekt darstellt und aus der entsprechenden verwalteter Code Schnittstelle abgerufen werden kann.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Legt den Wert dieses Objekts auf den Wert eines Objekts angegebenen verwalteten Code fest.|  
  
## Hinweise  
 Eine Auswertung eines Ausdrucks verwendet diese Schnittstelle, um verwaltete Codeobjekt in eine Analysestruktur zu speichern.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Bewerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)