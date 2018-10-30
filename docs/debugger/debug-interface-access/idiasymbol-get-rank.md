---
title: 'Idiasymbol:: Get_rank | Microsoft-Dokumentation'
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
ms.openlocfilehash: fc12e9251bd452edc3fdede1a5f7414462162301
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847694"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Ruft den Rang (Anzahl der Dimensionen) eines mehrdimensionalen Arrays von FORTRAN ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Dimensionen in ein mehrdimensionales Array von FORTRAN zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Rang bezieht sich auf die Anzahl der Dimensionen in einem Array, in dem das Array, als deklariert ist `myarray[1,2,3]`. In diesem Beispiel hat den Rang 3 und 3 Dimensionen. Rang gelten nicht für C++ das Konzept eines Arrays von Arrays für die einzelnen Dimensionen verwendet (d. h. `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)