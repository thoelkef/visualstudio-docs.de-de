---
title: 'Idiasymmetribol:: get_isStripped | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStripped method
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12fac0c26c53695dcc9b42794337a7feaea6b0fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740019"
---
# <a name="idiasymbolget_isstripped"></a>IDiaSymbol::get_isStripped
Ruft das Flag ab, das angibt, ob Private Symbole aus der Symbol Datei entfernt wurden.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isStripped(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Gibt `TRUE` zurück, wenn private Symbole aus der Symbol Datei entfernt wurden. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft ist über den `SymTagExe`-Symboltyp verfügbar (siehe [exe](../../debugger/debug-interface-access/exe.md)).

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Exe](../../debugger/debug-interface-access/exe.md)