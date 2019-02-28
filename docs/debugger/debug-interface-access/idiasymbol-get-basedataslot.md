---
title: IDiaSymbol::get_baseDataSlot | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f9ed21b7-9397-4813-926e-ade11914b06b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35612c8b4ab4e4ee64673d6058143788f56339fb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624125"
---
# <a name="idiasymbolgetbasedataslot"></a>IDiaSymbol::get_baseDataSlot
Ruft ab, die Basisdaten-Slot.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_baseDataSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Ein Zeiger auf eine `DWORD` , enthält den Basis Datenslot.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)