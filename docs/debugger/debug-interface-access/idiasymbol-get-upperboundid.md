---
title: 'Idiasymbol:: Get_upperboundid | Microsoft-Dokumentation'
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
ms.openlocfilehash: d0f3f0936982d91617674b43c7eaffc078ff098f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616742"
---
# <a name="idiasymbolgetupperboundid"></a>IDiaSymbol::get_upperBoundId
Ruft den Symbol-Bezeichner, der die obere Grenze einer FORTRAN Arraydimension ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_upperBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`
- [out] Gibt die ID des Symbols, der die obere Grenze einer FORTRAN Array Dimension darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
 Der Bezeichner ist ein eindeutiger Wert erstellt, das DIA SDK alle Symbole als eindeutig kennzeichnen.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)