---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736799"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Gibt die Informationen an, die über ein Stapelrahmenobjekt abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Felder
`FIF_FUNCNAME`\
Initialisieren/verwenden `m_bstrFuncName` Sie das Feld.

`FIF_RETURNTYPE`\
Initialisieren/verwenden `m_bstrReturnType` Sie das Feld.

`FIF_ARGS`\
Initialisieren/verwenden `m_bstrArgs` Sie das Feld.

`FIF_LANGUAGE`\
Initialisieren/verwenden `m_bstrLanguage` Sie das Feld.

`FIF_MODULE`\
Initialisieren/verwenden `m_bstrModule` Sie das Feld.

`FIF_STACKRANGE`\
Initialisieren/Verwenden `m_addrMin` der `m_addrMax` und (Stapelbereich) Felder.

`FIF_FRAME`\
Initialisieren/verwenden `m_pFrame` Sie das Feld.

`FIF_DEBUGINFO`\
Initialisieren/verwenden `m_fHasDebugInfo` Sie das Feld.

`FIF_STALECODE`\
Initialisieren/verwenden `m_fStaleCode` Sie das Feld.

`FIF_ANNOTATEDFRAME`\
Initialisieren/verwenden `m_fAnnotatedFrame` Sie das Feld.

`FIF_DEBUG_MODULEP`\
Initialisieren/verwenden `m_pModule` Sie das Feld.

`FIF_FUNCNAME_FORMAT`\
Formatiert den Funktionsnamen. Das Ergebnis wird `m_bstrFunName` im Feld zurückgegeben, und es werden keine anderen Felder ausgefüllt.

`FIF_FUNCNAME_RETURNTYPE`\
Fügt dem `m_bstrFuncName` Feld den Rückgabetyp hinzu.

`FIF_FUNCNAME_ARGS`\
Fügt dem `m_bstrFuncName` Feld die Argumente hinzu.

`FIF_FUNCNAME_LANGUAGE`\
Fügt dem `m_bstrFuncName` Feld die Sprache hinzu.

`FIF_FUNCNAME_MODULE`\
Fügt dem `m_bstrFuncName` Feld den Modulnamen hinzu.

`FIF_FUNCNAME_LINES`\
Fügt dem `m_bstrFuncName` Feld die Anzahl der Zeilen hinzu.

`FIF_FUNCNAME_OFFSET`\
Fügt dem `m_bstrFuncName` Feld den Offset in Bytes vom `FIF_FUNCNAME_LINES` Anfang der Zeile hinzu, wenn angegeben. Wenn `FIF_FUNCNAME_LINES` nicht angegeben ist oder wenn keine Zeilennummern verfügbar sind, fügt der Offset in Bytes vom Anfang der Funktion hinzu.

`FIF_FUNCNAME_ARGS_TYPES`\
Fügt dem `m_bstrFuncName` Feld den Typ jedes Funktionsarguments hinzu.

`FIF_FUNCNAME_ARGS_NAMES`\
Fügt dem `m_bstrFuncName` Feld den Namen jedes Funktionsarguments hinzu.

`FIF_FUNCNAME_ARGS_VALUES`\
Fügt dem `m_bstrFuncName` Feld den Wert jedes Funktionsarguments hinzu.

`FIF_FUNCNAME_ARGS_ALL`\
Fügt dem `m_bstrFuncName` Feld den Typ, den Namen und den Wert aller Argumente hinzu.

`FIF_ARGS_TYPES`\
Die Argumenttypen werden abgerufen und formatiert.

`FIF_ARGS_NAMES`\
Die Argumentnamen werden abgerufen und formatiert.

`FIF_ARGS_VALUES`\
Die Argumentwerte werden abgerufen und formatiert.

`FIF_ARGS_ALL`\
Abrufen und Formatieren des Typs, des Namens und des Wertes aller Argumente.

`FIF_ARGS_NOFORMAT`\
Gibt an, dass die Argumente nicht formatiert werden (z. B. fügen Sie keine öffnenden und schließenden Klammern um die Argumentliste hinzu oder fügen Sie ein Trennzeichen zwischen Argumenten hinzu).

`FIF_ARGS_NO_FUNC_EVAL`\
Gibt an, dass die Funktion (Eigenschafts-)Auswertung beim Abrufen von Argumentwerten nicht verwendet werden soll.

`FIF_FILTER_NON_USER_CODE`\
Das Debugmodul soll Nicht-Benutzercoderahmen filtern, damit sie nicht enthalten sind.

`FIF_ARGS_NO_TOSTRING`\
Keine `ToString()` Funktionsauswertung oder -formatierung zulassen, wenn Funktionsargumente zurückgegeben werden.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Frameinformationen sollten von der gehosteten App-Domäne und nicht vom Hostingprozess erhalten werden.

## <a name="remarks"></a>Bemerkungen
Diese Flags werden an die [EnumFrameInfo-](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) und [GetInfo-Methoden](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) übergeben, um anzugeben, welche Felder in der [FRAMEINFO-Struktur](../../../extensibility/debugger/reference/frameinfo.md) oder -Strukturen initialisiert werden sollen.

Diese Flags werden auch verwendet, um anzugeben, welche Felder der [FRAMEINFO-Struktur](../../../extensibility/debugger/reference/frameinfo.md) verwendet werden und gültig sind, wenn die Struktur zurückgegeben wird. Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
