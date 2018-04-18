---
title: 'Idialinenumber:: Get_statement | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: a2e28e5cf7588f0785c65803849610f27753dd81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
Ruft ein Flag gibt an, dass diese Zeileninformationen Anfang ein Ausdruck, in den Programmquellcode ein, anstatt eine Anweisung beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` Wenn diese Zeileninformationen den Anfang einer Anweisung in den Programmquellcode ein beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 -Anweisungen können mehrere Zeilen umfassen. Diese Methode gibt an, ob die zugeordnete Zeilennummer Anfang eine solche Anweisung mehrzeilige markiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)