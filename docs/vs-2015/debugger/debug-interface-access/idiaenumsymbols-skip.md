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
ms.openlocfilehash: e7a6a3f06572392cad2edbf125d0ff6491b508c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563701"
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