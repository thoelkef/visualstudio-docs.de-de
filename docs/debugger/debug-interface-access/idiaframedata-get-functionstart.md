---
title: 'Idiaframedata:: Get_functionstart | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6be173020e4aeb3b69197a038b4bc6d66c7eedc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908300"
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
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es ist möglich, dass ein Stapelrahmen entspricht nicht dem Anfang einer Funktion sein, da es sich bei den Frame einer Inlinemethode oder Funktion, die in einer Funktion eingefügt darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)