---
title: IEnumDebugPropertyInfo2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0eecb16ce4eecf4e39163a82c3aed48d35db6af2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933970"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Diese Schnittstelle listet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um Informationen für eine bestimmte Eigenschaft darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) beim Abrufen der diese Schnittstelle, die die untergeordneten Elemente einer bestimmten Eigenschaft darstellt. Rufen Sie [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) beim Abrufen der diese Schnittstelle, die die Eigenschaften eines bestimmten Stapelrahmens darstellen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugPropertyInfo2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Ruft eine angegebene Anzahl von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einer Enumerationsfolge.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Überspringt eine angegebene Anzahl von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einer Enumerationsfolge.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Ruft die Anzahl der [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einem Enumerator.|  
  
## <a name="remarks"></a>Hinweise  
 Im Allgemeinen ist eine Eigenschaft einer Hierarchie von Informationen, die ein Name, der Wert, der Adresse und der Typ enthalten kann, sowie andere Informationen für die zugeordnete Eigenschaft Objekt oder Stack-Frame. Finden Sie unter [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Weitere Details.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)