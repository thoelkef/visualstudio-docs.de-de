---
title: 'Idiasymbol:: Get_isstatic | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStatic method
ms.assetid: 3be5fe1b-46e8-4b07-90d8-4929dbbe7ff7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0cd30a8a1bcdab93f59c439cf27fce5049ebc09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899148"
---
# <a name="idiasymbolgetisstatic"></a>IDiaSymbol::get_isStatic
Ruft ein Flag, das angibt, ob die Funktion oder Thunk-Schicht als statisch markiert wurde.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_isStatic(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Gibt `TRUE` gibt zurück, wenn die Funktion oder Thunk-Schicht als statische, andernfalls markiert wurde, `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)