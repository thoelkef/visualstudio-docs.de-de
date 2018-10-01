---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8c40b0c28ce99d009a46aa02893dde2f5956c2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521188"
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaSymbol::get_isAcceleratorGroupSharedLocal](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal).  
  
Ruft ein Flag, das angibt, ob das Symbol auf eine freigegebene lokale Gruppenvariable im Code für eine C++-AMP-Beschleuniger kompiliert entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Ein Zeiger auf eine `BOOL` , der angibt, ob das Symbol auf eine freigegebene lokale Gruppenvariable im Code für eine C++-AMP-Beschleuniger kompiliert entspricht. Wenn `TRUE`, `get_baseDataSlot` und `get_baseDataOffset` Methoden können verwendet werden, um die Speicherortinformationen für die Variable abzurufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)



