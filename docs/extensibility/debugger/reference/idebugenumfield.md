---
title: IDebugEnumField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4df4e61b570460daca88bb65b38d5c681a5bea59
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930224"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Diese Schnittstelle stellt einen Enumerationstyp dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein symbolanbieter implementiert diese Schnittstelle, um eine Enumeration darstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) gibt `FIELD_TYPE_ENUM`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in VTable-Reihenfolge  
 Zusätzlich zu den Methoden für die `IDebugField` und `IDebugContainerField` Schnittstellen, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , das die den Namen für den Enumerationstyp.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Gibt den Namen der Enumerationskonstante, die den angegebenen Wert zugeordnet.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Gibt den Wert mit den Namen der angegebenen Enumeration-Konstante|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Gibt den Wert mit dem angegebene Enumeration-constant-Namen, aber Groß-/Kleinschreibung ignorieren.|  
  
## <a name="remarks"></a>Hinweise  
 Es ist das zugrunde liegende Symbol, das tatsächlich an einen Speicherort mit gebunden wird [binden](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)