---
title: 'Idiaframedata:: Get_type | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90a7096550dc3de67ba38058c4029a6bd3c30ca4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611489"
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Ruft den compilerspezifischen Frametyp ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt einen Wert aus der [StackFrameTypeEnum-Enumeration](../../debugger/debug-interface-access/stackframetypeenum.md) -Enumeration, die den compilerspezifischen Frametyp angibt.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [StackFrameTypeEnum-Enumeration](../../debugger/debug-interface-access/stackframetypeenum.md)