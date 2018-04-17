---
title: IDebugField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2ff92f339568a6a20e2f85a0b2deae9c8db244f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfield"></a>IDebugField
Diese Schnittstelle stellt ein Feld, d. h. eine Beschreibung eines Symbols oder einen Typ dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol-Anbieter implementiert diese Schnittstelle als Basisklasse für alle Felder.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist die Basisklasse für alle Felder. Basierend auf den Rückgabewert der [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), diese Schnittstelle möglicherweise spezialisiertere Schnittstellen zurückgeben, indem [QueryInterface](/cpp/atl/queryinterface). Darüber hinaus zahlreiche Schnittstellen zurückgeben `IDebugField` Objekte aus verschiedenen Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugField`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ruft die anzeigbaren Informationen über das Symbol oder den Typ ab.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ruft die Art des Felds ab.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ruft den Typ des Felds ab.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ruft den Container des Felds ab.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ruft die Adresse des Felds ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ruft die Größe eines Felds in Bytes ab.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ruft Informationen zu einem Feld erweitert.|  
|[Gleich](../../../extensibility/debugger/reference/idebugfield-equal.md)|Vergleicht zwei Felder an.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ruft die typunabhängig Informationen über das Symbol oder den Typ ab.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Typ ist äquivalent zu einer C#-Sprache `typedef`.  
  
 Im folgenden C++-Sprache-Beispiel `weather` ist ein Klassentyp und `sunny` und `stormy` Symbole sind:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Ob ein Feld, ein Symbol darstellt oder Typ kann, durch den Aufruf bestimmt werden [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) und untersucht werden, die [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Ergebnis. Wenn die `FIELD_KIND_TYPE` Bit festgelegt ist, das Feld ein, und wenn die `FIELD_KIND_SYMBOL` Bit festgelegt ist, es ist ein Symbol.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)