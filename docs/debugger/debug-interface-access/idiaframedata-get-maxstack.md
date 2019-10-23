---
title: 'IDiaFrameData:: get_maxStack | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc5eaa20c5167897ccb19d5e142656ed314a91e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743527"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
Ruft die maximale Anzahl von Bytes ab, die auf dem Stapel im Frame abgelegt werden.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die maximale Anzahl von Bytes zurück, die auf dem Stapel abgelegt werden.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der von dieser Methode zurückgegebene Wert wird in der Regel in der Interpretation einer Programm Zeichenfolge verwendet (Weitere Informationen finden Sie in der [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) -Methode für die Definition einer Programm Zeichenfolge).

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)