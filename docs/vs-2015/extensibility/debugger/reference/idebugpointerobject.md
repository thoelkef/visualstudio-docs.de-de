---
title: IDebugPointerObject | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 217136135c7fec71065f6a18e156ff2e5e956499
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524918"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPointerObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerobject).  
  
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt ein Zeigerobjekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung implementiert diese Schnittstelle, um ein Zeigerobjekt darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann diese Schnittstelle abrufen, indem Sie mithilfe von [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) Wenn die `IDebugObject` stellt einen Zeiger dar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugPointerObject` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ruft das Objekt ab, das die Schnittstelle verweist.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ruft den Wert, den die Schnittstelle als eine Reihe von aufeinander folgenden Bytes verweist.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Legt den Wert, den die Schnittstelle aus einer Reihe von aufeinander folgenden Bytes verweist.|  
  
## <a name="remarks"></a>Hinweise  
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um einen Zeiger in eine Analysestruktur darzustellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

