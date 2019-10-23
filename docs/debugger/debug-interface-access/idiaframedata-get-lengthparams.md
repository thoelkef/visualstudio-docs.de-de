---
title: 'IDiaFrameData:: get_lengthParams | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthParams method
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aca86590dd214214df671e084925e02e611d521d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743569"
---
# <a name="idiaframedataget_lengthparams"></a>IDiaFrameData::get_lengthParams
Ruft die Anzahl der Bytes von Parametern ab, die auf dem Stapel abgelegt werden.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Anzahl der Bytes von Parametern zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der von dieser Methode zurückgegebene Wert wird in der Regel in der Interpretation einer Programm Zeichenfolge verwendet (Weitere Informationen finden Sie in der [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) -Methode für die Definition einer Programm Zeichenfolge).

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)