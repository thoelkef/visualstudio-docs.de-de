---
title: 'Idiasymmetribol:: get_symTag | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symTag method
ms.assetid: 139a35bd-faeb-4878-be72-394dedfbb18f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99f24e47ff04c6a7d37633c4f04bbd058b861cd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739228"
---
# <a name="idiasymbolget_symtag"></a>IDiaSymbol::get_symTag
Ruft den Symboltyp Klassifizierer ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_symTag ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt einen Wert aus der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -enumerationsenumeration zurück, der den Symboltyp Klassifizierer angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="example"></a>Beispiel

```C++
IDiaSymbol* pType;
DWORD       tag = 0;
pType->get_symTag( &tag );
```

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)