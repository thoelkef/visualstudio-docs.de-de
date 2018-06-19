---
title: 'Idialinenumber:: Get_statement | Microsoft Docs'
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
ms.openlocfilehash: c259c7157ad98dee3830e96ca8922b88a2fe56c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459674"
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