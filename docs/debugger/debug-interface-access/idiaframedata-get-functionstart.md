---
title: 'Idiaframedata:: Get_functionstart | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7f532b55ffd401b88471921cb41d47410604dfa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939373"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
Ruft ein Flag, das angibt, ob der Block den Einstiegspunkt einer Funktion enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn der Block den Einstiegspunkt; enthält andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es ist möglich, dass ein Stapelrahmen entspricht nicht dem Anfang einer Funktion sein, da es sich bei den Frame einer Inlinemethode oder Funktion, die in einer Funktion eingefügt darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)