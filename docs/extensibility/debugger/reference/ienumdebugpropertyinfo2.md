---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715350"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Diese Schnittstelle zählt [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um Informationen für eine bestimmte Eigenschaft darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) auf, um diese Schnittstelle zu erhalten, die die untergeordneten Elemente einer bestimmten Eigenschaft darstellt. Rufen Sie [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) auf, um diese Schnittstelle abzurufen, die die Eigenschaften eines bestimmten Stapelrahmens darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugPropertyInfo2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Ruft eine angegebene Anzahl von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Überspringt eine angegebene Anzahl von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Ruft die Anzahl der [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Im Allgemeinen ist eine Eigenschaft eine Hierarchie von Informationen, die einen Namen, Wert, Adresse und Typ sowie alle anderen Informationen enthalten kann, die für das zugeordnete Eigenschaftenobjekt oder den zugeordneten Stapelrahmen geeignet sind. Weitere Informationen finden Sie unter [IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
