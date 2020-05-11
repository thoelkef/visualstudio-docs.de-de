---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c260b6316207b0079a2ca8893b851db8b1288ba6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728307"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Diese Schnittstelle stellt eine abstrakte Position einer Funktion in einem Quelldokument dar.

## <a name="syntax"></a>Syntax

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle, um die Position einer Funktion in einem Quelldokument darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird als Teil einer [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union (insbesondere einer [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Struktur) bereitgestellt, die wiederum Teil der [BP_REQUEST_INFO-Struktur](../../../extensibility/debugger/reference/bp-request-info.md) ist, die zum Erstellen eines ausstehenden Haltepunkts verwendet wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugFunctionPosition2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ruft den Namen der Funktion ab, zu der diese Position relativ ist.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Ruft den Offset vom Anfang der Funktion ab.|

## <a name="remarks"></a>Bemerkungen
 Die Position, die durch diese Schnittstelle dargestellt wird, ist textbasiert, insbesondere eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
