---
title: 'Idiasymbol:: Get_container | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ca0b183f0616705ec61475c4570fa11ce89640d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622279"
---
# <a name="idiasymbolgetcontainer"></a>IDiaSymbol::get_container
Diese Funktion ruft einen Zeiger auf ein Symbol, das den übergeordneten/Container dieses Symbols darstellt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt einen Zeiger auf ein `IDiaSymbol` mit Informationen über den Container, der dieses Symbol.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. andernfalls S_FALSE oder ein Fehlercode.

> [!NOTE]
>  Ein Rückgabewert von S_FALSE bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)