---
title: 'Idiaframedata:: Get_lengthparams | Microsoft-Dokumentation'
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
ms.openlocfilehash: 712f7ee9eaf497fc5dd176f3f254d5af73ebcf3b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620238"
---
# <a name="idiaframedatagetlengthparams"></a>IDiaFrameData::get_lengthParams
Ruft die Anzahl der Bytes von Parametern, die auf dem Stapel abgelegt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt die Anzahl der Bytes von Parametern zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
 Der von dieser Methode zurückgegebene Wert wird normalerweise verwendet, bei der Interpretation einer Programm-Zeichenfolge (finden Sie unter den [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) -Methode für die Definition einer Programm-Zeichenfolge).

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)