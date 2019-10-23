---
title: 'Idiasymmetribol:: get_lowerBoundId | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBoundId method
ms.assetid: 12ce98e9-a225-4947-88c9-5fda39dd67e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d3685512521d5fc919f4c9b1752a039ae1085bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739826"
---
# <a name="idiasymbolget_lowerboundid"></a>IDiaSymbol::get_lowerBoundId
Ruft den Symbol Bezeichner der unteren Grenze einer Fortran-Array Dimension ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_lowerBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Symbol-ID des Symbols zurück, das die untere Grenze einer Fortran-Array Dimension darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Der Bezeichner ist ein eindeutiger Wert, der vom Dia SDK erstellt wird, um alle Symbole als eindeutig zu markieren.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)