---
title: IDebugField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a036f6d08c6f88a30f8a8c9ab6d0d2e847065854
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682919"
---
# <a name="idebugfield"></a>IDebugField
Diese Schnittstelle stellt ein Feld, d. h. eine Beschreibung eines Symbols oder Typ.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein symbolanbieter implementiert diese Schnittstelle als Basisklasse für alle Felder ein.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle ist die Basisklasse für alle Felder. Basierend auf den Rückgabewert der [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), diese Schnittstelle möglicherweise weitere spezialisierte Schnittstellen zurückgeben, indem [QueryInterface](/cpp/atl/queryinterface). Darüber hinaus viele Schnittstellen zurückgeben `IDebugField` Objekte aus verschiedenen Methoden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugField`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ruft die anzeigbare Informationen über das Symbol oder einen Typ ab.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ruft die Art des Felds ab.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ruft den Typ des Felds ab.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ruft den Container des Felds ab.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ruft die Adresse des Felds ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ruft die Größe eines Felds in Bytes ab.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ruft Informationen über ein Feld erweitert werden.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Vergleicht zwei Felder an.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ruft die typunabhängig-Informationen über das Symbol oder einen Typ ab.|

## <a name="remarks"></a>Hinweise
 Ein Typ ist gleichbedeutend mit einer C#-Sprache `typedef`.

 Im folgenden C++-Sprache-Beispiel `weather` ist ein Klassentyp und `sunny` und `stormy` Symbole sind:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Ob ein Feld, ein Symbol darstellt oder Typ werden, indem bestimmt kann [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) und Untersuchen der [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Ergebnis. Wenn die `FIELD_KIND_TYPE` Bit ist gesetzt, wird das Feld ein, und wenn die `FIELD_KIND_SYMBOL` Bit ist gesetzt, es ist ein Symbol.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)