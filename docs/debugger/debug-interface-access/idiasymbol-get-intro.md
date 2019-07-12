---
title: 'Idiasymbol:: Get_intro | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 153daa1f43ba4945a5eb32aea82c5d58ff57c5f6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836799"
---
# <a name="idiasymbolgetintro"></a>IDiaSymbol::get_intro
Ruft ein Flag, das angibt, ob die Funktion eine Einführung in virtuelle Funktion ist ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
`pRetVal`

[out] Gibt `TRUE` , wenn die Funktion Einführung virtuellen; ist andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="example"></a>Beispiel

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Beide `A::f1` und `B::f1` sind virtuelle Funktionen, aber `A::f1` Einführung virtuell ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK V7. 0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
