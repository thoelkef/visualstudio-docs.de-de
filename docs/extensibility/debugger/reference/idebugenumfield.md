---
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7885f36a113809e81279498a769e257af4f1cde2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730172"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Diese Schnittstelle stellt einen Enumerationstyp dar.

## <a name="syntax"></a>Syntax

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle, um eine Enumeration darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um diese Schnittstelle von der `FIELD_TYPE_ENUM` [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) abzuholen, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt.

## <a name="methods-in-vtable-order"></a>Methoden in VTable-Reihenfolge
 Zusätzlich zu den Methoden `IDebugField` `IDebugContainerField` auf der und Schnittstellen implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Gibt ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Namen für diesen Enumerationstyp beschreibt.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Gibt den Namen der Enumerationskonstante zurück, die dem angegebenen Wert zugeordnet ist.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Gibt den Wert zurück, der dem angegebenen Enumerationskonstantennamen zugeordnet ist.|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Gibt den Wert zurück, der dem angegebenen Enumerationskonstantennamen zugeordnet ist, aber die Groß-/Kleinschreibung ignoriert wird.|

## <a name="remarks"></a>Bemerkungen
 Es ist das zugrunde liegende Symbol, das tatsächlich an einen Speicherort mit [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)gebunden ist.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)
