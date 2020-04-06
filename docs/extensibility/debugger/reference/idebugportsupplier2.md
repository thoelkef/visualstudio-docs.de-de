---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724475"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Diese Schnittstelle stellt Ports für den Sitzungsdebug-Manager (SDM) bereit.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle, um einen Portlieferanten darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
Ein Aufruf `CoCreateInstance` an mit einem `GUID` Portlieferanten gibt diese Schnittstelle zurück (dies ist der typische Weg, um diese Schnittstelle zu erhalten). Beispiel:

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

Ein Aufruf von [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) gibt diese Schnittstelle zurück, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]die den aktuellen Portlieferanten darstellt, der von verwendet wird.

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) gibt diese Schnittstelle zurück, die den Portlieferanten darstellt, der den Port erstellt hat.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) stellt eine `IDebugPortSupplier` Liste von `IEnumDebugPortSuppliers` Schnittstellen dar (die Schnittstelle wird von [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)abgerufen, die alle mit [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]registrierten Portlieferanten darstellt).

Ein Debugmodul interagiert in der Regel nicht mit einem Portlieferanten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt `IDebugPortSupplier2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ruft den Portlieferantennamen ab.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Ruft den Portlieferantenbezeichner ab.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Ruft einen Port von einem Portlieferanten ab.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Zählt die bereits vorhandenen Ports auf.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Überprüft, ob ein Portlieferant das Hinzufügen neuer Ports unterstützt.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Fügt einen Port hinzu.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Entfernt einen Port.|

## <a name="remarks"></a>Bemerkungen
Ein Portlieferant kann sich anhand von Name und ID identifizieren, Ports hinzufügen und entfernen und alle Ports aufzählen, die der Portlieferant bereitstellt.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
