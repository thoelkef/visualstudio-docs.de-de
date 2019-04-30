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
ms.openlocfilehash: fb3caa5574605864a0dd16b59b6f451530b8e631
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827787"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Gibt eine Enumeration von Symbolen für Inlineframes, die für den Namen der Funktion Inline angegeben.

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

[in] Der Funktionsname des Inlinees, gesucht werden soll.

 `option`

[in] Die Name-Suchoptionen zum Suchen verwendet werden, wenn die Suche nach Inline frames entsprechen `name`. Weitere Informationen finden Sie unter [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

[out] Ein Zeiger auf ein `IDiaEnumSymbols` Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Funktion sucht nach Ihren Inlinees zuzuordnen sind, nur innerhalb von Accelerator-Stub-Funktionen. Native C++-Prozedur Datensätze werden ignoriert.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)