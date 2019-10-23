---
title: 'IDiaFrameData:: get_lengthProlog | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthProlog method
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b85d1db996487d76d396d6e4df9ea557e6aae5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743562"
---
# <a name="idiaframedataget_lengthprolog"></a>IDiaFrameData::get_lengthProlog
Ruft die Anzahl der Bytes des prologcodes im-Block ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_lengthProlog ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Anzahl der Bytes des prologcodes zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Bei dem Prologcode handelt es sich um eine Sequenz von Anweisungen, die Register beibehält, den CPU-Status festlegt und den Stapel für die Funktion festlegt.

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)