---
title: IEnumDebugAddresses | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac02ca2f22b95b35cc12a545debf081c4052d520
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867559"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Diese Schnittstelle stellt eine Auflistung von Objekten, die Implementierung der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.

## <a name="syntax"></a>Syntax

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird implementiert, von der symbolanbieter zu Gruppen von Objekten, die implementieren die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle. Beachten Sie, dass dies keine standard-COM-Enumeration durch das Vorhandensein der [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) Methode.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird durch zurückgegeben [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) und [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgenden Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Ruft den nächsten Satz von [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekte aus der Enumeration.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Setzt die Enumeration an den ersten Eintrag zurück.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Ruft eine Kopie der aktuellen Enumeration.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle wird von der Debug-Engine in der Regel verwendet, um zu ermitteln, die entsprechende Adresse auf die ausdrucksauswertung gewähren.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)