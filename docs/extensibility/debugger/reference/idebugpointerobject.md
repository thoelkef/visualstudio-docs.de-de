---
title: IDebugPointerObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 42467738a12105f4631020d0b6d5b4f62d1dc95b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt einen Zeigerobjekt dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung implementiert diese Schnittstelle, um ein Mauszeiger-Objekt darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann mithilfe dieser Schnittstelle abrufen [QueryInterface](/cpp/atl/queryinterface) Wenn die `IDebugObject` stellt einen Zeiger dar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugPointerObject` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Dereferenzierung](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ruft das Objekt ab, das die Schnittstelle verweist.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ruft den Wert, den die Schnittstelle als eine Reihe von aufeinander folgenden Bytes verweist.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Legt den Wert, den die Schnittstelle von einer Reihe von aufeinander folgenden Bytes verweist.|  
  
## <a name="remarks"></a>Hinweise  
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um einen Zeiger in einen Analysestruktur darzustellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)