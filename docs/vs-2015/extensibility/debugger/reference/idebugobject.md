---
title: IDebugObject | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 157e4ef5a6f8875a85de1108f94028ef25d25075
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956902"
---
# <a name="idebugobject"></a>IDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt ein Objekt, das der Binder erstellt wird, um die Werte der Symbole und Ausdrücke zu kapseln.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine ausdrucksauswertung implementiert diese Schnittstelle, um ein Objekt darstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist die Basisklasse für alle Objekte, die die ausdrucksauswertung analysiert Ausdrücke verwendet. Er wird zurückgegeben, durch einen Aufruf der [binden](../../../extensibility/debugger/reference/idebugbinder-bind.md) Methode. [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) erhält die spezialisierteren Schnittstellen von dieser Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugObject`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Ruft die Größe des Objekts ab.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Ruft den Wert des Objekts als eine aufeinanderfolgende Reihe von Bytes ab.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Legt den Wert des Objekts aus eine aufeinanderfolgende Reihe von Bytes fest.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Legt den Verweiswert, der dieses Objekt.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Ruft ab, der Arbeitsspeicher-Kontext, der die Adresse des Werts des Objekts darstellt.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Erstellt eine Kopie des verwalteten Objekts im Adressraum der Debug-Engine.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testet, ob dieses Objekt ein null-Verweis ist.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Vergleicht ein Objekt in dieses Objekt.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Bestimmt, ob dieses Objekt schreibgeschützt ist.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Bestimmt, ob das Objekt über einen transparenten Proxy ist.|  
  
## <a name="remarks"></a>Hinweise  
 Die ausdrucksauswertung verwendet diese Schnittstelle als Basisklasse verwendet, um Objekte in eine Analysestruktur darzustellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)
