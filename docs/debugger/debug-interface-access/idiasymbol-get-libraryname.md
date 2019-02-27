---
title: 'Idiasymbol:: Get_libraryname | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_libraryName method
ms.assetid: d04ddd9a-812d-46e4-bd39-28bdf3edfb70
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f832bc0472cc6b04d803dc1e5871eda62bbe451d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605639"
---
# <a name="idiasymbolgetlibraryname"></a>IDiaSymbol::get_libraryName
Ruft ab, der Dateiname, der die Bibliothek oder Objektdatei, die aus der das Objekt geladen wurde.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_libraryName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt den Dateinamen, der die Bibliothek oder Objektdatei, die aus der das Objekt geladen wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)