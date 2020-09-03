---
title: IEnumDebugPortSuppliers2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715932"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Mit dieser Schnittstelle werden Port Lieferanten aufgelistet.

## <a name="syntax"></a>Syntax

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Visual Studio implementiert, um eine Liste von Port Anbietern darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie " [enumportsuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) " auf, um eine Liste der Port Lieferanten zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugPortSuppliers2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Ruft eine angegebene Anzahl von Port Anbietern in einer Enumerationsfolge ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Überspringt eine angegebene Anzahl von Port Lieferanten in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Ruft die Anzahl der Port Lieferanten in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Eine Debug-Engine muss diese Schnittstelle in der Regel nicht abrufen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
