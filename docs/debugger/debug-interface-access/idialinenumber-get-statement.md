---
title: 'Idialinenumber:: Get_statement | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c6b16d142f5bdc83b9a16e3299c15a0c845cf2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949322"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
Ruft ein Flag, das angibt, dass diese Zeileninformationen wird, den Anfang einer Anweisung, anstatt ein Ausdruck, in der Programmquelle beschrieben ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` Wenn diese Zeileninformationen den Beginn einer Anweisung in der Programmquelle beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 -Anweisungen können mehrere Zeilen umfassen. Diese Methode gibt an, ob die zugeordnete Zeilennummer den Anfang der solche eine mehrzeilige Anweisung markiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)