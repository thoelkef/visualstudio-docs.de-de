---
title: IEnumCodePaths2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fd34b88324fa2e2121fa46b637cb0ec0d26d35a
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223398"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Diese Schnittstelle stellt eine Liste der Codepfade.

## <a name="syntax"></a>Syntax

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um eine Liste von Codepfaden darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) dieser Schnittstelle abgerufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IEnumCodePaths2`.

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Ruft eine angegebene Anzahl von Codepfade in einer Enumerationsfolge ab.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Überspringt eine angegebene Anzahl von Codepfade in einer Enumerationsfolge.|
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Ruft die Anzahl der Codepfade in einen Enumerator ab.|

## <a name="remarks"></a>Hinweise
 Ein Codepfad stellt eine Verzweigung Punkt oder einen Funktionsaufruf in einem Programm dar. Eine Liste der Codepfade stellt dar, den Pfad, über dem Ausführung des Codes stattgefunden hat.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)