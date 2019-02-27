---
title: IDiaSymbol::get_textureSlot | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 166a1a3a-2e10-4baa-ace1-9104b56185ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b480cfee85af750addddbbc195881adab002e07c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598894"
---
# <a name="idiasymbolgettextureslot"></a>IDiaSymbol::get_textureSlot
Ruft ab, der Textur-Slot.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_textureSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Ein Zeiger auf eine `DWORD` , enthält den Textur-Slot.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)