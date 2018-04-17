---
title: IDebugFunctionObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e7281be40e7559171c82da81d89f717bea3c8ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt eine Funktion dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine ausdrucksauswertung implementiert diese Schnittstelle, um eine Funktion darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist eine Spezialisierung der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Benutzeroberfläche und mit abgerufen wird [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugObject` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Ein primitiver Datenobjekt erstellt.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Erstellt ein Objekt mit einem Konstruktor.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Erstellt ein Objekt mit kein Konstruktor an.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Erstellt ein Arrayobjekt.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Erstellt ein String-Objekt.|  
|[Auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Ruft die Funktion und gibt den resultierenden Wert als ein Objekt zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ermöglicht die ausdrucksauswertung zur Darstellung von Funktionen in einer Analysestruktur. Die `Create` Methoden in dieser Schnittstelle zum Erstellen von Objekten, die die Eingabeparameter der Methode darstellen. Die Funktion kann dann ausgeführt werden, durch Aufrufen der [auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) Methode, die ein Objekt, das den Rückgabewert der Funktion darstellt zurückgibt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)