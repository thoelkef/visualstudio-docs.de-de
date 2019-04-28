---
title: 'Idiaframedata:: Get_maxstack | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bacefc74c4699ef2d2d75ff7ca7af47a56cfb44b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562888"
---
# <a name="idiaframedatagetmaxstack"></a>IDiaFrameData::get_maxStack
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die maximale Anzahl von Bytes, die auf dem Stapel im Frame abgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die maximale Anzahl von Bytes, die auf dem Stapel abgelegt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der von dieser Methode zurückgegebene Wert wird normalerweise verwendet, bei der Interpretation einer Programm-Zeichenfolge (finden Sie unter den [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) -Methode für die Definition einer Programm-Zeichenfolge).  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
