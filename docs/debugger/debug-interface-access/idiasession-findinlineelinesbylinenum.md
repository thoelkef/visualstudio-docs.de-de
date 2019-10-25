---
title: 'IDiaSession:: findinlineelinesbylinenum | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe238f3bc66d6a7c5978c5d7cbebcd185fcd43d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742212"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt in der angegebenen Quelldatei und Zeilennummer Inline sind, durchlaufen kann.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 column,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `compiland`

in Ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das die Kompilierungen darstellt, in der nach den Zeilennummern gesucht werden soll. Dieser Parameter kann nicht `NULL` werden.

 `file`

in Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekt, das die Quelldatei darstellt, in der gesucht werden soll. Dieser Parameter kann nicht `NULL` werden.

 `linenum`

in Gibt eine einzeilige Zeilennummer an.

> [!NOTE]
> Sie können keine NULL-Werte verwenden, um alle Zeilen anzugeben (verwenden Sie die [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) -Methode, um alle Zeilen zu finden).

 `column`

in Gibt die Spaltennummer an. Verwenden Sie 0 (null), um alle Spalten anzugeben. Eine Spalte ist ein Byte Offset in eine Zeile.

 `ppResult`

vorgenommen Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt zurück, das eine Liste der abgerufenen Zeilennummern enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)