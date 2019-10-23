---
title: 'Idiasymmetribol:: get_registerType | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e849bea3bd5480f480001c091e5988fa5e6b5444
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739437"
---
# <a name="idiasymbolget_registertype"></a>IDiaSymbol::get_registerType
Ruft den registriungstyp ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_registerType(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Ein Zeiger auf eine `DWORD`, die den Registertyp enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)