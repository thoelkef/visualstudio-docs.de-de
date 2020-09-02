---
title: Idebugpointerobject | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4cd84c3580d94491e09ce9e8cde8175f9e437be0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693402"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt ein Zeiger Objekt dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Ausdrucks Auswertung implementiert diese Schnittstelle, um ein Zeiger Objekt darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle kann diese Schnittstelle mithilfe von [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) abrufen, wenn der `IDebugObject` einen Zeiger darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden, die von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md)geerbt werden, stellt die- `IDebugPointerObject` Schnittstelle die folgenden Methoden zur Verfügung.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ruft das-Objekt ab, auf das die-Schnittstelle zeigt.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ruft den Wert ab, auf den die Schnittstelle als Folge von aufeinander folgenden Bytes zeigt.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Legt den Wert fest, auf den die Schnittstelle aus einer Reihe von aufeinander folgenden Bytes zeigt.|  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Ausdrucks Auswertung verwendet diese Schnittstelle, um einen Zeiger in einer Analyse Struktur darzustellen.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucks Bewertungs Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
