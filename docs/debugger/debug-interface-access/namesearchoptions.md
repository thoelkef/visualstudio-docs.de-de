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
ms.openlocfilehash: 8fa637a5f403a4651541d920c6390204ee579994
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318614"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Gibt die Suchoptionen für Symbol und den Dateinamen an.

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
`nsNone`  
Es wurden keine Optionen angegeben.

`nsfCaseSensitive`  
Wendet eine namensübereinstimmung der Groß-/Kleinschreibung an.

`nsfCaseInsensitive`  
Wendet eine namensübereinstimmung der Groß-/Kleinschreibung an.

`nsfFNameExt`  
Namen behandelt, als Pfade und eine namensübereinstimmung filename.ext gilt.

`nsfRegularExpression`  
Wendet die Groß-/Kleinschreibung namensübereinstimmung mithilfe von Sternchen (*) und Fragezeichen (?) als Platzhalter.

`nsfUndecoratedName`  
Gilt nur für Symbole, die nicht ergänzten Form und ergänzte Namen haben.

## <a name="remarks"></a>Anmerkungen
Die Werte aus dieser Enumeration werden für die folgenden Methoden übergeben:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Anforderungen
Header: dia2.h

## <a name="see-also"></a>Siehe auch
[Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
