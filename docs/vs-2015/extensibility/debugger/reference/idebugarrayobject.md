---
title: IDebugArrayObject | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfee8f9a0d3aae1fdfe63c93bd49b9f3f5dc5c2b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290978"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt ein Arrayobjekt dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung implementiert diese Schnittstelle, um ein Array darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann diese Schnittstelle abrufen, indem Sie mithilfe von [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , wenn das Objekt ein Array darstellt.  
  
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
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um Arrays in eine Analysestruktur darzustellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

