---
title: IDebugArrayField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a16be2cd972688ef27816caacba2b5b0cfb53d4b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885652"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Diese Schnittstelle wird beschrieben, ein Array Symbol oder einen Typ.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Der symbolanbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle. Diese Schnittstelle ist eine Spezialisierung, die Array von Objekten darstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) gibt das Flag zurück `FIELD_TYPE_ARRAY`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) und [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstellen, die diese Schnittstelle implementiert die folgenden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Ruft die Anzahl der Elemente im Array ab.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Ruft den Typ des Elements im Array ab.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Ruft den Rang des Arrays ab.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)