---
title: 'IDiaSession:: findinlineelines | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5103a881b1b046479a1a3156f06038e230f5063e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742242"
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
Ruft eine Enumeration ab, die es einem Client ermöglicht, die Zeilennummern Informationen aller Funktionen zu durchlaufen, die direkt oder indirekt durch das angegebene übergeordnete Symbol Inline sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineeLines ( 
   IDiaSymbol*       parent,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `parent`

in Ein `IDiaSymbol`-Objekt, das das übergeordnete Element darstellt.

 `ppResult`

vorgenommen Enthält ein `IDiaEnumLineNumbers` Objekt, das die Liste der abgerufenen Zeilennummern enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)