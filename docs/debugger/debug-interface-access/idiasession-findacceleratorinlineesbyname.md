---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742310"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Gibt eine Enumeration von Symbolen für Inline Frames zurück, die dem angegebenen Inline Funktionsnamen entsprechen.

## <a name="syntax"></a>Syntax

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parameter
 `name`

in Der Name der inlinees-Funktion, die durchsucht werden soll.

 `option`

in Die namens Suchoptionen, die beim Suchen nach Inline Frames verwendet werden sollen, die `name` entsprechen. Weitere Informationen finden Sie unter [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

vorgenommen Ein Zeiger auf einen `IDiaEnumSymbols` Schnittstellen Zeiger, der mit dem Ergebnis initialisiert wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Funktion sucht inlinees zuzuordnen sind nur innerhalb von Accelerator-Stub-Funktionen. Systemeigene C++ Prozeduren werden ignoriert.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)