---
title: 'Idiaframedata:: Get_allocatesbasepointer | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdeab20ee39dc62688f7cf4604e00117d9eb676f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Ruft ein Flag, das angibt, ob der basiszeiger für Code in diesem Adressbereich zugeordnet ist. Diese Methode ist veraltet.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn ein basiszeiger zugeordnet ist; andernfalls wird `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft sollte verwendet werden, nur von Code, die früher auf FPO_DATA zugegriffen werden soll, oder wenn die Programm-Zeichenfolge zurückgegeben, durch, die [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) Methode ist `NULL`. Andernfalls enthält die Zeichenfolge für die Anwendung alle Informationen, die zum Berechnen der vorherigen Registerwerte benötigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)