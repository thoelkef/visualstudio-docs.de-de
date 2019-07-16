---
title: 'Idialinenumber:: Get_compiland | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25d990ab019c01daf1f977464211fb72838275a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829044"
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
Ruft einen Verweis auf das Symbol für der Kompiliereinheit, das die Bytes des Image Text beigetragen hat.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parameter
 pRetVal

[out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt für der Kompiliereinheit, das die Bytes des Image Text beigetragen hat.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)