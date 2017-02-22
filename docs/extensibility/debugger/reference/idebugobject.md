---
title: "IDebugObject | Microsoft Docs"
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
  - "IDebugObject"
helpviewer_keywords: 
  - "IDebugObject-Schnittstelle"
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt ein Objekt, das der Binder erstellt, um die Werte von Symbolen und Ausdrücke zu kapseln.  
  
## Syntax  
  
```  
IDebugObject : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Ausdrucksauswerter implementiert diese Schnittstelle, um ein Objekt darstellt.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle ist die Basisklasse für alle Objekte, die die Auswertung eines Ausdrucks in analysierten Ausdrücken verwendet. Rückgabe durch einen Aufruf der [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md) Methode.[QueryInterface](/visual-cpp/atl/queryinterface) Ruft die spezifischen Schnittstellen von dieser Schnittstelle ab.  
  
## Methoden in Vtable\-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugObject`.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Ruft die Größe des Objekts.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Ruft den Wert des Objekts als eine fortlaufende Folge von Bytes ab.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Legt den Wert des Objekts über eine fortlaufende Folge von Bytes fest.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Legt den Wert dieses Objekts fest.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Ruft den Arbeitsspeicher\-Kontext, der die Adresse des Werts des Objekts darstellt.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Erstellt eine Kopie des verwalteten Objekts im Adressraum des Debugging\-Modul.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testet, ob dieses Objekt einen null\-Verweis ist.|  
|[\[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Vergleicht ein Objekt dieser Klasse.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Bestimmt, ob dieses Objekt schreibgeschützt ist.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Bestimmt, ob das Objekt einen transparenten Proxy ist.|  
  
## Hinweise  
 Die Auswertung eines Ausdrucks verwendet diese Schnittstelle als Basisklasse, um Objekte in eine Analysestruktur darzustellen.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)