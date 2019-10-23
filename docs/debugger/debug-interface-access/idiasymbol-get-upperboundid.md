---
title: 'Idiasymmetribol:: get_upperBoundId | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBoundId method
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 640bce657df53bec66ab75575f35fcd68131a82a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738940"
---
# <a name="idiasymbolget_upperboundid"></a>IDiaSymbol::get_upperBoundId
Ruft den Symbol Bezeichner der oberen Grenze einer Fortran-Array Dimension ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_upperBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`
- [out,] Gibt die ID des Symbols zurück, das die obere Grenze einer Fortran-Array Dimension darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Der Bezeichner ist ein eindeutiger Wert, der vom Dia SDK erstellt wird, um alle Symbole als eindeutig zu markieren.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)