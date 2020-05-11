---
title: IEnumDebugPortLieferanten2 | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715932"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Diese Schnittstelle zählt Portlieferanten auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle, um eine Liste von Portlieferanten darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) auf, um eine Liste der Hafenlieferanten zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugPortSuppliers2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Ruft eine angegebene Anzahl von Portlieferanten in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Überspringt eine angegebene Anzahl von Portlieferanten in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Ruft die Anzahl der Portlieferanten in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Debugmodul muss diese Schnittstelle in der Regel nicht abrufen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
