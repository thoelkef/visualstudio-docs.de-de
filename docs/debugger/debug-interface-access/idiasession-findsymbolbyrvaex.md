---
title: 'IDiaSession:: findSymbolByRVAEx | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9b27cee1c8df3eb26d64f4f860c33e0d4bf45f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742036"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
Ruft einen angegebenen Symboltyp ab, der eine angegebene relative virtuelle Adresse (RVA) und einen Offset enthält bzw. am nächsten liegt.

## <a name="syntax"></a>Syntax

```C++
HRESULT findSymbolByRVAEx ( 
   DWORD        rva,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>Parameter
 `rva`

in Gibt die RVA an.

 `symtag`

in Symboltyp, der gefunden werden soll. Werte werden aus der Enumeration der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) entnommen.

 `ppSymbol`

vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das das abgerufene Symbol darstellt.

 `displacement`

vorgenommen Gibt einen Wert zurück, der einen Offset von der in `rva` angegebenen relativen virtuellen Adresse angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)