---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717716"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Diese Schnittstelle stellt eine Liste von Codepfaden dar.

## <a name="syntax"></a>Syntax

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um eine Liste von Codepfaden darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumCodePaths2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Ruft eine angegebene Anzahl von Codepfaden in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Überspringt eine angegebene Anzahl von Codepfaden in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Ruft die Anzahl der Codepfade in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Codepfad stellt einen Verzweigungspunkt oder Funktionsaufruf in einem Programm dar. Eine Liste von Codepfaden stellt den Pfad dar, den die Codeausführung durchlaufen hat.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
