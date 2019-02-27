---
title: IDiaSession::findAcceleratorInlineesByLinenum | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a2f23c42de99e0ea9a9d6c50e2d9aabed589d4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611151"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Gibt eine Enumeration von Symbolen für Inlineframes, die entsprechen zum Speicherort angegebenen Quelle zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   IDiaSymbol*           parent,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 colnum,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `parent`

[in] Ein `IDiaSymbol` , entspricht die Accelerator-Stub-Funktion, die durchsucht werden soll.

 `file`

[in] Die `IDiaSourceFile` des Quellspeicherorts.

 `linenum`

[in] Die Nummer der Zeile des Quellspeicherorts.

 `colnum`

[in] Die Spaltennummer des Quellspeicherorts.

 `ppResult`

[out] Ein Zeiger auf ein `IDiaEnumLineNumbers` Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)