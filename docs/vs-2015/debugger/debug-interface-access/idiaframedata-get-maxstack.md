---
title: 'IDiaFrameData:: get_maxStack | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562888"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die maximale Anzahl von Bytes ab, die auf dem Stapel im Frame abgelegt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt die maximale Anzahl von Bytes zurück, die auf dem Stapel abgelegt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der von dieser Methode zurückgegebene Wert wird in der Regel in der Interpretation einer Programm Zeichenfolge verwendet (Weitere Informationen finden Sie in der [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) -Methode für die Definition einer Programm Zeichenfolge).  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
