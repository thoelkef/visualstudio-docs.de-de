---
title: IDebugAddress2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66fd149bc3eed7633586c156f6493c8febcbeaac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330360"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Diese Schnittstelle bietet Zugriff auf die ID des Prozesses, der das Objekt, dessen Adresse besitzt, die von dieser Schnittstelle dargestellt wird.

## <a name="syntax"></a>Syntax

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein symbolanbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle. Diese Schnittstelle bietet Zugriff auf die ID des Prozesses, der das Objekt besitzt, das an diese Adresse verknüpft ist.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von geerbten Methoden der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle, die diese Schnittstelle implementiert, die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Ruft die ID des Prozesses, der Besitzer des Objekts, das von dieser Schnittstelle dargestellt ist.|

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)