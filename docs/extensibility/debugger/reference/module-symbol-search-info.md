---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714246"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Enthält Statusinformationen zu Symbolsuchpfaden, die durchsucht wurden.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Member

`dwValidFields`\
Eine Kombination von [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Flags aus der SYMBOL_SEARCH_INFO_FIELDS-Enumeration, die die Art der in dieser Struktur beschriebenen Suchinformationen angibt.

`bstrVerboseSearchInfo`\
Suchpfad und Ergebnisse, die zu einer einzelnen Zeichenfolge verkettet sind.

## <a name="remarks"></a>Bemerkungen

Diese Struktur wird von einem Aufruf der [GetSymbolInfo-Methode](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) zurückgegeben.

Wenn `bstrVerboseSearchInfo` das Feld nicht leer ist, enthält es eine Liste der gesuchten Pfade und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad formatiert, gefolgt von einer Auslassung ("..."), gefolgt vom Ergebnis. Wenn mehr als ein Pfadergebnispaar vorhanden ist, wird jedes Paar durch ein Paar "-r-n" (Carriage-Return/linefeed) getrennt. Das Muster sieht wie folgt aus:

\<Pfad>... \<Ergebnis> Pfad\<>... \<Ergebnis\<>-Pfad>... \<Ergebnis>

Beachten Sie, dass der letzte Eintrag keine Sequenz von .r.n.

Hier ist `bstrVerboseSearchInfo` eine mögliche Zeichenfolge, die an Standard-Out gesendet wurde.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Requirements (Anforderungen)

Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
