---
title: 'Idiaenumsymbols:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea2b1ea99eb2801259d58a12c359e9fffd887a64
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641209"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Überspringt eine angegebene Anzahl von Symbolen in einer Enumerationsfolge.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 celt

[in] Die Anzahl der Symbole in der Enumerationsfolge übersprungen werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` treten keine Symbole mehr, um zu überspringen.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)