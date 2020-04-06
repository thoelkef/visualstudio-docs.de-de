---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 402d8c8bcb50c570ff680b8fe1cf8d26f037ba17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736570"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Diese Schnittstelle bietet Zugriff auf die ID des Prozesses, der Eigentümer des Objekts ist, dessen Adresse durch diese Schnittstelle dargestellt wird.

## <a name="syntax"></a>Syntax

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugAddress-Schnittstelle](../../../extensibility/debugger/reference/idebugaddress.md) implementiert. Diese Schnittstelle bietet Zugriff auf die ID des Prozesses, der das Objekt besitzt, das mit dieser Adresse verknüpft ist.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um diese Schnittstelle von der [IDebugAddress-Schnittstelle](../../../extensibility/debugger/reference/idebugaddress.md) abzufragen.

## <a name="methods-in-vtable-order"></a>Methoden in vtable Order
 Zusätzlich zu den Methoden, die von der [IDebugAddress-Schnittstelle](../../../extensibility/debugger/reference/idebugaddress.md) geerbt wurden, implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Ruft die ID des Prozesses ab, dem das Objekt gehört, das durch diese Schnittstelle dargestellt wird.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
