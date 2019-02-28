---
title: 'Idiasymbol:: Get_compilergenerated | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerGenerated method
ms.assetid: 864d9249-f0c8-4a34-b391-eb785f7e8865
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39c3751eb71d3d0e627946212ee5aaa54c1b5253
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623111"
---
# <a name="idiasymbolgetcompilergenerated"></a>IDiaSymbol::get_compilerGenerated
Ruft ein Flag, das angibt, ob das Symbol vom Compiler generiert wurde.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_compilerGenerated ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` , wenn der Compiler, das Symbol generiert; andernfalls `FALSE` , wenn das Symbol von benutzerspezifischen Quelle generiert wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK V7. 0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)