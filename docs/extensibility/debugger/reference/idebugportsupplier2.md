---
title: IDebugPortSupplier2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ffb759c2f3309351f9c27feb719e18c49a39ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871525"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Diese Schnittstelle stellt die Ports für die Sitzung Debug-Manager (SDM) bereit.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um eines portanbieters darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Ein Aufruf von `CoCreateInstance` mit eines portanbieters `GUID` gibt diese Schnittstelle (Dies ist das übliche Verfahren zum Abrufen dieser Schnittstelle). Zum Beispiel:

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

Ein Aufruf von [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) gibt diese Schnittstelle, die der aktuelle anschlusslieferant vom verwendeten darstellt [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) gibt diese Schnittstelle, die Sie die Port-Lieferanten, der der Port erstellt darstellt.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) stellt eine Liste von `IDebugPortSupplier` Schnittstellen (die `IEnumDebugPortSuppliers` Schnittstelle aus einer [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), registriert,dieallediePortanbieterdarstellen[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).

Eine Debug-Engine in der Regel nicht mit eines portanbieters interagieren.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt die Methoden der `IDebugPortSupplier2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ruft den Namen der Port-Lieferanten.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Ruft die Port-Lieferanten-ID ab.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Ruft einen Port aus eines portanbieters ab.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Listet die Ports, die bereits vorhanden.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Stellt sicher, dass ein portanbieters unterstützt das Hinzufügen von neuen Ports ein.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Fügt einen Port an.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Entfernt einen Port an.|

## <a name="remarks"></a>Hinweise
Ein portanbieters kann sich selbst identifizieren, durch den Namen und die ID, hinzufügen und Entfernen von Ports, und Auflisten von allen Ports, die der Anschlusslieferanten bereitstellt.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
