---
title: 'IDiaLineNumber:: get_statement | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a37052944f74e36b488541074a0033f5b8aca9e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743128"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Ruft ein Flag ab, das angibt, dass diese Zeilen Informationen den Anfang einer Anweisung anstelle eines Ausdrucks in der Programmquelle beschreiben.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt `TRUE` zurück, wenn diese Zeilen Informationen den Anfang einer Anweisung in der Programmquelle beschreiben.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 -Anweisungen können sich über mehrere Zeilen erstrecken. Diese Methode gibt an, ob die zugeordnete Zeilennummer den Anfang einer solchen mehrzeiligen Anweisung kennzeichnet.

## <a name="see-also"></a>Siehe auch
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)