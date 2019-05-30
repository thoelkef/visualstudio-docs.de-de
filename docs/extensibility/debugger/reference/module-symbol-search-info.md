---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c521ebe321813013b83a951d4d2aa5f60fd1646d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346616"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO

Enthält Statusinformationen zu Symbolsuchpfade, die durchsucht wurden.

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
Eine Kombination von Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) -Enumeration, die die Art der Suche Informationen, die in dieser Struktur beschriebenen angibt.

`bstrVerboseSearchInfo`\
Suchpfad und Ergebnisse in einer einzelnen Zeichenfolge verkettet.

## <a name="remarks"></a>Hinweise

Diese Struktur wird zurückgegeben, von einem Aufruf der ["getsymbolinfo"](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) Methode.

Wenn die `bstrVerboseSearchInfo` Feld nicht leer ist, und es enthält eine Liste von Pfaden, die durchsucht und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad, gefolgt von einer mit den Auslassungspunkten ("…"), gefolgt von das Ergebnis formatiert. Wenn mehr als ein Paar der Path-Ergebnis vorhanden ist, wird jedes Paar von ein Paar aus "\r\n" (Wagenrücklauf/Zeilenvorschub) getrennt. Das Muster sieht folgendermaßen aus:

\<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis >

Beachten Sie, dass der letzte Eintrag nicht mit eine Sequenz \r\n verfügt.

Hier ist eine mögliche `bstrVerboseSearchInfo` Zeichenfolge, die an die Standardausgabe gesendet wurde.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Anforderungen

Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch

- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)