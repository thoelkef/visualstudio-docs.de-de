---
title: IEnumDebugFields | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f557b722a36665b20f5e06093027f8085a014ed
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716752"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Diese Schnittstelle stellt eine Auflistung von Objekten, die Implementierung der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.

## <a name="syntax"></a>Syntax

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird implementiert, von der symbolanbieter zu Gruppen von Objekten, die implementieren die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle. Beachten Sie, dass dies keine standard-COM-Enumeration durch das Vorhandensein der [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) Methode.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird durch zurückgegeben [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) und [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgenden Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Ruft den nächsten Satz von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekte aus der Enumeration.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Setzt die Enumeration an den ersten Eintrag zurück.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Ruft eine Kopie der aktuellen Enumeration.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|

## <a name="remarks"></a>Hinweise

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)