---
title: 'Idiaframedata:: Get_lengthlocals | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_lengthLocals method
ms.assetid: 51fe15c3-4cd6-4a06-8a41-a56502209762
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9548bc86eba94ddb7f857deb4cd066e400d5bfb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagetlengthlocals"></a>IDiaFrameData::get_lengthLocals
Ruft die Anzahl der Bytes von lokalen Variablen, die auf dem Stapel abgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_lengthLocals (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Bytes der lokalen Variablen zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Von dieser Methode zurückgegebene Wert wird üblicherweise in die Interpretation einer Zeichenfolge für die Anwendung verwendet (finden Sie unter der [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) Methode für die Definition einer Anwendung Zeichenfolge).  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)