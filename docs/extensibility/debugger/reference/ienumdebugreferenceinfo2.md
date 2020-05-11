---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715271"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Diese Schnittstelle zählt [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle als Teil ihrer Unterstützung für Verweise auf Objekte im Speicher. Diese Schnittstelle darf nur implementiert werden, wenn Verweise unterstützt werden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Visual Studio ruft [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugReferenceInfo2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Ruft eine angegebene Anzahl von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Überspringt eine angegebene Anzahl von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in der Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Ruft die Anzahl der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Verweis ist im Wesentlichen ein Typ und eine Adresse, während eine Eigenschaft ein Name, Typ und Adresse ist. Ein Verweis bleibt bestehen, solange das Objekt, auf das verwiesen wird, im Arbeitsspeicher vorhanden ist. Weitere Informationen finden Sie unter [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
