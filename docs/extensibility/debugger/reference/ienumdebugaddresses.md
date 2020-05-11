---
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717585"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Diese Schnittstelle stellt eine Auflistung von Objekten dar, die die [IDebugAddress-Schnittstelle](../../../extensibility/debugger/reference/idebugaddress.md) implementieren.

## <a name="syntax"></a>Syntax

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird vom Symbolanbieter implementiert, um Gruppen von Objekten bereitzustellen, die die [IDebugAddress-Schnittstelle](../../../extensibility/debugger/reference/idebugaddress.md) implementieren. Beachten Sie, dass dies keine Standard-COM-Enumeration aufgrund des Vorhandenseins der [GetCount-Methode](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) ist.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird von [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) und [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)zurückgegeben.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgenden Methoden.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Ruft den nächsten Satz von [IDebugAddress-Objekten](../../../extensibility/debugger/reference/idebugaddress.md) aus der Enumeration ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Setzt die Enumeration auf den ersten Eintrag zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Ruft eine Kopie der aktuellen Enumeration ab.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird in der Regel vom Debugmodul verwendet, um die geeignete Adresse zu bestimmen, die dem Ausdrucksauswertungswert geber.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
