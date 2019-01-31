---
title: 'Idiaframedata:: Get_allocatesbasepointer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3aa3150efe4dffb1df2090e8381d471c720c690
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009777"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Ruft ein Flag, das angibt, ob der basiszeiger für Code in dieser Adressbereich zugeordnet ist. Diese Methode ist veraltet.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn ein basiszeiger zugeordnet ist; andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft sollte verwendet werden, nur von Code, die früher auf FPO_DATA zugegriffen werden soll, oder wenn die Programm-Zeichenfolge zurückgegeben, durch, die [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) Methode `NULL`. Die Programm-Zeichenfolge enthält, andernfalls die Informationen, die zum Berechnen des vorherigen Registerwerte erforderlich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)