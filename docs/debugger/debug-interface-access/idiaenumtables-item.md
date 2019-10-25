---
title: 'IDiaEnumTables:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743755"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Ruft eine Tabelle mithilfe eines Indexes oder Namens ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Parameter
 `index`

in Der Index oder Name der zu abzurufenden [idisierbaren](../../debugger/debug-interface-access/idiatable.md) . Wenn eine ganzzahlige Variante verwendet wird, muss Sie im Bereich von 0 bis `count`-1 liegen, wobei `count` von der [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) -Methode zurückgegeben wird.

 `table`

vorgenommen Gibt ein [idisierbares](../../debugger/debug-interface-access/idiatable.md) Objekt zurück, das die gewünschte Tabelle darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn eine Zeichen folgen Variante angegeben wird, benennt die Zeichenfolge eine bestimmte Tabelle. Der Name muss einer der Tabellennamen sein, wie in [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)definiert.

## <a name="example"></a>Beispiel

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Siehe auch
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)