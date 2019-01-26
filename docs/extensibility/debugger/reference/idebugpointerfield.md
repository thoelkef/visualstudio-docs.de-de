---
title: IDebugPointerField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ef1b83dba8e35a1eee1c26090cc965b6afa41f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015536"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Diese Schnittstelle stellt einen Zeiger dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die symbolanbieter implementiert diese Schnittstelle, um einen Zeiger darstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) gibt `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die `IDebugField` und `IDebugContainerField` Schnittstellen, die diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , beschreibt das Ziel des Zeigers.|  
  
## <a name="remarks"></a>Hinweise  
 In C/C++ kann ein Zeiger auf einen Container sein, wenn sie mit der Arraynotation verwendet wird. Angenommen, `char *pString`, `pString` verfügt über einen Typ eines Zeigers auf den `char`. `pString[3]` weist den Typ des einem Container ist ein Zeiger auf `char` , die auf das vierte Element der diesem Container verweist.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)