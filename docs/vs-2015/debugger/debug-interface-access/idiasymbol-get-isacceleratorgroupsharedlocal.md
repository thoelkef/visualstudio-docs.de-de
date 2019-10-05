---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2e975f75d25e64925c2566c1c311d942e9c3766
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "68180991"
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, das angibt, ob das Symbol auf eine freigegebene lokale Gruppenvariable im Code für eine C++-AMP-Beschleuniger kompiliert entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Ein Zeiger auf eine `BOOL` , der angibt, ob eine freigegebene lokale Gruppenvariable in Code kompiliert wird, für das Symbol entspricht einem C++ Ampaccelerator. Wenn `TRUE`, `get_baseDataSlot` und `get_baseDataOffset` Methoden können verwendet werden, um die Speicherortinformationen für die Variable abzurufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)
