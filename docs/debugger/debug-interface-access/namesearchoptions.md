---
title: NameSearchOptions | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c2b06e8d89405b38afe2b740ce860a78bc46cc
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661812"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Gibt die Suchoptionen für Symbol-und Dateinamen an.

## <a name="syntax"></a>Syntax

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Elements
`nsNone` Es wurden keine Optionen angegeben.

`nsfCaseSensitive`Wendet eine namens Übereinstimmung nach Groß-/Kleinschreibung

`nsfCaseInsensitive`Wendet die Groß-/Kleinschreibung nicht an.

`nsfFNameExt`Behandelt Namen als Pfade und wendet eine filename. ext-namens Übereinstimmung an.

`nsfRegularExpression`Wendet eine namens Übereinstimmung unter Berücksichtigung der Groß-/Kleinschreibung mithilfe von Sternchen (*) und Fragezeichen (?) als Platzhalter an. (Andere gängige Zeichen für reguläre Ausdrücke werden nicht unterstützt.)

`nsfUndecoratedName`Gilt nur für Symbole mit nicht ergänzten und ergänzten Namen.

## <a name="remarks"></a>Hinweise
Die Werte aus dieser Enumeration werden an die folgenden Methoden übermittelt:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Anforderungen
Header: dia2.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
