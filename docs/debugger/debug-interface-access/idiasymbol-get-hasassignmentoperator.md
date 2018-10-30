---
title: 'Idiasymbol:: Get_hasassignmentoperator | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAssignmentOperator method
ms.assetid: fb1acb9c-4500-4343-a590-0395789e4040
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 855f0379a416bab1f05ebec390fe54399feefba9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850008"
---
# <a name="idiasymbolgethasassignmentoperator"></a>IDiaSymbol::get_hasAssignmentOperator
Ruft ein Flag, das angibt, ob der benutzerdefinierte Datentyp Zuweisungsoperatoren definiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_hasAssignmentOperator (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn der benutzerdefinierte Datentyp Zuweisungsoperatoren definiert wurde, andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK V7. 0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)