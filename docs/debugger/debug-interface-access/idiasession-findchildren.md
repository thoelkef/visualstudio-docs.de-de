---
title: 'IDiaSession:: findChildren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca6778e5697c5f8821322c19d706d733d7f2b9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742299"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Ruft alle untergeordneten Elemente eines angegebenen übergeordneten Bezeichners ab, die dem Namen und dem Symboltyp entsprechen.

## <a name="syntax"></a>Syntax

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `parent`

in Ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das das übergeordnete Element darstellt. Wenn dieses übergeordnete Symbol eine Funktion, ein Modul oder ein Block ist, werden die lexikalischen untergeordneten Elemente in `ppResult` zurückgegeben. Wenn das übergeordnete Symbol ein Typ ist, werden die untergeordneten Klassen der Klasse zurückgegeben. Wenn dieser Parameter `NULL` ist, muss `symtag` auf `SymTagExe` oder `SymTagNull` festgelegt werden, wodurch der globale Gültigkeitsbereich (exe-Datei) zurückgegeben wird.

 `symtag`

in Gibt das symboltag der untergeordneten Elemente an, die abgerufen werden sollen. Werte werden aus der Enumeration der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) entnommen. Legen Sie `SymTagNull` fest, um alle untergeordneten Elemente abzurufen.

 `name`

in Gibt den Namen der untergeordneten Elemente an, die abgerufen werden sollen. Legen Sie auf `NULL` fest, damit alle untergeordneten Elemente abgerufen werden.

 `compareFlags`

in Gibt die auf die namens Übereinstimmung angewendeten Vergleichs Optionen an Werte aus der Enumeration-Enumeration von [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) können allein oder in Kombination verwendet werden.

 `ppResult`

vorgenommen Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt zurück, das die Liste der abgerufenen untergeordneten Symbole enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gezeigt, wie lokale Variablen der Funktions `pFunc` gefunden werden, die mit Name `szVarName` identisch sind.

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>Siehe auch
- [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)