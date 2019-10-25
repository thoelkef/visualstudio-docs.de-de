---
title: 'Idiasymmetribol:: findinlineelinesbyaddr | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1709120dfa8e115f4b14a4ee4e2d1c7ffb293329
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741223"
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt in diesem Symbol innerhalb des angegebenen Adress Bereichs angeordnet sind, durchlaufen kann.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineeLinesByAddr ( 
   DWORD                 isect,
   DWORD                 offset,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
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
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)