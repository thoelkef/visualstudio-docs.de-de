---
title: IDiaSymbol::get_uavSlot | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35ca770550df55766856792d1495b167cb02a11c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734044"
---
# <a name="idiasymbolgetuavslot"></a>IDiaSymbol::get_uavSlot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Uav-Slot ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_uavSlot(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `DWORD` , enthält den Uav-Slot.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



