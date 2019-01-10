---
title: IDiaSymbol::get_textureSlot | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 166a1a3a-2e10-4baa-ace1-9104b56185ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ed21168c053e90d83f5377367e565d54b71467f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910979"
---
# <a name="idiasymbolgettextureslot"></a>IDiaSymbol::get_textureSlot
Ruft ab, der Textur-Slot.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_textureSlot(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `DWORD` , enthält den Textur-Slot.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)