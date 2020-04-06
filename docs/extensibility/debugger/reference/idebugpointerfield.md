---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725596"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Diese Schnittstelle stellt einen Zeigertyp dar.

## <a name="syntax"></a>Syntax

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Symbolanbieter implementiert diese Schnittstelle, um einen Zeiger darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um diese Schnittstelle von der `FIELD_TYPE_POINTER` [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) abzuholen, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden `IDebugField` `IDebugContainerField` auf der und Schnittstellen implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Gibt ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, das das Ziel des Zeigers beschreibt.|

## <a name="remarks"></a>Bemerkungen
 In C/C++ kann ein Zeiger ein Container sein, wenn er mit Arraynotation verwendet wird. Beispielsweise verfügt `char *pString`given `pString` über einen Zeiger `char`typ auf . `pString[3]`hat den Typ eines Containers, der `char` ein Zeiger darauf ist, der auf das vierte Element dieses Containers verweist.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
