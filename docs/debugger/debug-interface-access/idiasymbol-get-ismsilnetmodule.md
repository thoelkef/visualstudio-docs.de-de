---
title: 'Idiasymmetribol:: get_isMSILNetmodule | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isMSILNetmodule method
ms.assetid: 593827f3-8437-4a12-ada4-ff715ec95fb2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 322a4ef059c190e3ba73bbce6f80978530270ece
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740187"
---
# <a name="idiasymbolget_ismsilnetmodule"></a>IDiaSymbol::get_isMSILNetmodule
Ruft ein Flag ab, das angibt, ob es sich bei dem Modul um ein netmodule-Modul (ein MSIL-Modul (Microsoft Intermediate Language) handelt, das nur Metadaten und keine nativen Symbole enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isMSILNetmodule(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Gibt `TRUE` zurück, wenn das Modul MSIL ist. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft ist über den `SymTagCompilandDetails`-Symboltyp verfügbar (siehe [compilanddetails](../../debugger/debug-interface-access/compilanddetails.md)).

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)