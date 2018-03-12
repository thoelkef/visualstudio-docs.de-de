---
title: IDebugArrayObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7a447a54fa0fcbc686cee0229c4c8dc6e80eeb20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt ein Arrayobjekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung implementiert diese Schnittstelle, um ein Array darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann mithilfe dieser Schnittstelle abrufen [QueryInterface](/cpp/atl/queryinterface) , wenn das Objekt ein Array darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die `IDebugObject` -Schnittstelle, die folgenden Methoden werden implementiert, auf die `IDebugArrayObject` Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ruft die Anzahl der Elemente im Array ab.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Ruft ein Element des Arrays ab.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ruft alle Elemente des Arrays ab.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ruft den Rang des Arrays ab.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ruft die Dimensionen des Arrays ab.|  
  
## <a name="remarks"></a>Hinweise  
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um Arrays in einer Analysestruktur darzustellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)