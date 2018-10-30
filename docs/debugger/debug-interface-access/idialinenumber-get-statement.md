---
title: 'Idialinenumber:: Get_statement | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 4b1c2602f9336d5e59a9e692f13170aacf68a1c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947928"
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
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 -Anweisungen können mehrere Zeilen umfassen. Diese Methode gibt an, ob die zugeordnete Zeilennummer den Anfang der solche eine mehrzeilige Anweisung markiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)