---
title: 'Idiasymmetribol:: get_hasManagedCode | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasManagedCode method
ms.assetid: e40f82f5-88fe-4a9b-b594-3605f42773ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 79696a0f4476d8e8b571cb8b8c0cc5e181b11f92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740491"
---
# <a name="idiasymbolget_hasmanagedcode"></a>IDiaSymbol::get_hasManagedCode
Ruft ein Flag ab, das angibt, ob das Modul verwalteten Code enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_hasManagedCode(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Gibt `TRUE` zurück, wenn das Modul verwalteten Code enthält. Andernfalls wird `FALSE` zurückgegeben, der Code ist nicht verwalteter Code.

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