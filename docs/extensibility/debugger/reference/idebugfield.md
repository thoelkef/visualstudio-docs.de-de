---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728754"
---
# <a name="idebugfield"></a>IDebugField
Diese Schnittstelle stellt ein Feld dar, d. h. eine Beschreibung eines Symbols oder Typs.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle als Basisklasse für alle Felder.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle ist die Basisklasse für alle Felder. Basierend auf dem Rückgabewert von [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)kann diese Schnittstelle mithilfe von [QueryInterface](/cpp/atl/queryinterface)speziellere Schnittstellen zurückgeben. Darüber hinaus geben viele `IDebugField` Schnittstellen Objekte aus verschiedenen Methoden zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugField`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ruft anzeigebare Informationen über das Symbol oder den Typ ab.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ruft die Art des Felds ab.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ruft den Feldtyp ab.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ruft den Container des Felds ab.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ruft die Adresse des Felds ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ruft die Größe eines Felds in Bytes ab.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ruft erweiterte Informationen zu einem Feld ab.|
|[Gleich](../../../extensibility/debugger/reference/idebugfield-equal.md)|Vergleicht zwei Felder.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ruft typunabhängige Informationen über das Symbol oder den Typ ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Typ entspricht einer `typedef`C-Sprache .

 Im folgenden C++-Sprachbeispiel `weather` ist ein `sunny` Klassentyp und `stormy` Symbole:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Ob ein Feld ein Symbol oder einen Typ darstellt, kann durch Aufrufen von [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) und Untersuchen des [FIELD_KIND-Ergebnisses](../../../extensibility/debugger/reference/field-kind.md) bestimmt werden. Wenn `FIELD_KIND_TYPE` das Bit festgelegt ist, ist das `FIELD_KIND_SYMBOL` Feld ein Typ, und wenn das Bit gesetzt ist, ist es ein Symbol.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
