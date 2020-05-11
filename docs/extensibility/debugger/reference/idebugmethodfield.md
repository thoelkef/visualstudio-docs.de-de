---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727063"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Diese Schnittstelle beschreibt eine Methode.

## <a name="syntax"></a>Syntax

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugContainerField-Schnittstelle](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert. Diese Schnittstelle ist eine Spezialisierung, die eine Methode darstellt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um diese Schnittstelle von der `FIELD_TYPE_METHOD` [IDebugContainerField-Schnittstelle](../../../extensibility/debugger/reference/idebugcontainerfield.md) abzuholen, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt. Darüber hinaus geben die Methoden [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)und [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)die `IDebugMethodField` Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf den [Schnittstellen IDebugField](../../../extensibility/debugger/reference/idebugfield.md) und [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Erstellt einen Enumerator für die Parameter der Methode.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Ruft den "this"-Zeiger des Objekts ab, das die Methode enthält.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Erstellt einen Enumerator für alle lokalen Variablen der Methode.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Erstellt einen Enumerator für statische lokale Variablen der Methode.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Ruft den globalen Container der Methode ab.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Erstellt einen Enumerator für den Typ jedes Arguments, das zum Aufrufen der Methode erforderlich ist.|

## <a name="remarks"></a>Bemerkungen
 Eine Methode kann sowohl Parameter als auch lokale Variablen enthalten.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
