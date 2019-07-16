---
title: 'Idiasymbol:: Get_oemid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91d6097fd558ee3fd4e61485eb53cd25a0b7c6a2
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64796039"
---
# <a name="idiasymbolgetoemid"></a>IDiaSymbol::get_oemId
Ruft die ID-Wert für das Symbol des Originalgerätehersteller (OEM) ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_oemId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt einen eindeutigen Wert, der einen OEM identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft gilt nur für Symbole mit einem [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Typ `SymTagCustomType`.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)