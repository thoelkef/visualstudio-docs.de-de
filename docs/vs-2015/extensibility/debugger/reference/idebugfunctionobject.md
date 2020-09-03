---
title: Idebugfunctionobject | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 831cbb8f9416d37f87ecbed1a2da0c79531ee87f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690189"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt eine Funktion dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine Ausdrucks Auswertung implementiert diese Schnittstelle, um eine Funktion darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist eine Spezialisierung der [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle und wird mithilfe von [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) in der `IDebugObject` Schnittstelle abgerufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden, die von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md)geerbt werden, stellt die- `IDebugFunctionObject` Schnittstelle die folgenden Methoden zur Verfügung.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Erstellt ein Primitives Datenobjekt.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Erstellt ein-Objekt mithilfe eines Konstruktors.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Erstellt ein-Objekt ohne Konstruktor.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Erstellt ein Array Objekt.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Erstellt ein Zeichen folgen Objekt.|  
|[Evaluieren](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Ruft die-Funktion auf und gibt den resultierenden Wert als-Objekt zurück.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle ermöglicht der Ausdrucks Auswertung das darstellen von Funktionen in einer Analyse Struktur. Die `Create` Methoden in dieser Schnittstelle werden verwendet, um-Objekte zu erstellen, die die Eingabeparameter für die Methode darstellen. Die Funktion kann dann durch Aufrufen der Methode [Auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) ausgeführt werden, die ein Objekt zurückgibt, das den Rückgabewert der Funktion darstellt.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucks Bewertungs Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
