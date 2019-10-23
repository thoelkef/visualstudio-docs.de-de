---
title: 'Idiasymmetribol:: get_hfaDouble | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hfaDouble method
ms.assetid: efc247b9-c16e-4fa3-89b0-901caf7b74c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30a393f2725b4924a02bbaed12aef8b60273ffd0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740419"
---
# <a name="idiasymbolget_hfadouble"></a>IDiaSymbol::get_hfaDouble
Ruft ein Flag ab, das angibt, ob ein benutzerdefinierter Typ (User-Defined Type, UDT) homogene Gleit Komma Aggregatdaten (HFA) vom Typ Double enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_hfaDouble( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt `TRUE` zurück, wenn der UDT HFA-Daten des Typs "Double" enthält. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)