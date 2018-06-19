---
title: 'Idiaframedata:: Get_allocatesbasepointer | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: efbadae145fff951effc7413e432ab2570549c95
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31462001"
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