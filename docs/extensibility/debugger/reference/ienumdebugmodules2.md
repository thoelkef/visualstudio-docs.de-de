---
title: IEnumDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716442"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Diese Schnittstelle listet eine Liste von Modulen auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle, um eine Liste der für ein Programm geladenen Module darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Visual Studio ruft [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugModules2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Ruft eine angegebene Anzahl von Modulen in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Überspringt eine angegebene Anzahl von Modulen in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ruft die Anzahl der Module ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio verwendet diese Schnittstelle in erster Linie, um das **Modulfenster** zu aktualisieren.

 Für das Debuggen in Visual Studio ist ein Programm eine logische Folge von Codeanweisungen, die Modulgrenzen überschreiten können, daher ist eine Liste von Modulen für eine einzelne [IDebugProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogram2.md) erforderlich. Das erste Modul in der Liste enthält in der Regel den Anfangseinstiegspunkt für das zugeordnete Programm.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
