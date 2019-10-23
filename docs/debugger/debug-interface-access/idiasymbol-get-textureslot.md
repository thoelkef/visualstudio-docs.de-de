---
title: 'Idiasymmetribol:: get_textureSlot | Microsoft-Dokumentation'
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
ms.openlocfilehash: 92aa950447d46f2342fdbaa0114e2bec956cd5a5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739169"
---
# <a name="idiasymbolget_textureslot"></a>IDiaSymbol::get_textureSlot
Ruft den Textur Slot ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_textureSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Ein Zeiger auf eine `DWORD`, die den Textur Slot enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)