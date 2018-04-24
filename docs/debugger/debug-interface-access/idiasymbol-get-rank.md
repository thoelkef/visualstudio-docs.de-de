---
title: 'Idiasymbol:: Get_rank | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b78ba89b56c6d8c473060e39d402ee46e4ae15f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Ruft den Rang (Anzahl der Dimensionen) eines mehrdimensionalen Arrays FORTRAN ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Dimensionen in mehrdimensionalen Arrays FORTRAN zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Rang bezieht sich auf die Anzahl der Dimensionen in einem Array, in dem Deklarieren des Arrays als `myarray[1,2,3]`. Dieses Beispiel umfasst den Rang 3 und 3 Dimensionen. Rang gilt nicht für C++, die das Konzept eines Arrays von Arrays für jede Dimension verwendet (d. h. `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)