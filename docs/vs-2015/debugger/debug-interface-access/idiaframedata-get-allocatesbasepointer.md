---
title: 'Idiaframedata:: Get_allocatesbasepointer | Microsoft-Dokumentation'
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
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40a58fb764dd4700324f7c63e7f100982e297a34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210099"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, das angibt, ob der basiszeiger für Code in dieser Adressbereich zugeordnet ist. Diese Methode ist veraltet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn ein basiszeiger zugeordnet ist; andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft sollte verwendet werden, nur von Code, die früher auf FPO_DATA zugegriffen werden soll, oder wenn die Programm-Zeichenfolge zurückgegeben, durch, die [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) Methode `NULL`. Die Programm-Zeichenfolge enthält, andernfalls die Informationen, die zum Berechnen des vorherigen Registerwerte erforderlich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)



