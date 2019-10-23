---
title: 'IDiaSession:: findinlineelinesbyaddr | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496f6b569b3ac02c625ddf18406b78fdb1687be2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742234"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Ruft eine Enumeration ab, die es einem Client ermöglicht, die Zeilennummerinformationen aller Funktionen, die direkt oder indirekt durch das angegebene übergeordnete Symbol eingebunden sind, zu durchlaufen und innerhalb des angegebenen Adress Bereichs enthalten sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `parent`

in Ein `IDiaSymbol`-Objekt, das das übergeordnete Element darstellt.

 `isect`

in Gibt die Abschnitts Komponente der Adresse an.

 `offset`

in Gibt die Offset Komponente der Adresse an.

 `length`

in Gibt den Adressbereich in Byte an, der mit dieser Abfrage abgedeckt werden soll.

 `ppResult`

vorgenommen Enthält ein `IDiaEnumLineNumbers` Objekt, das die Liste der abgerufenen Zeilennummern enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)