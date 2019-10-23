---
title: 'IDiaFrameData:: get_functionStart | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 324cad63a597768dc2c13447c6d2d68756878695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743615"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
Ruft ein Flag ab, das angibt, ob der-Block den Einstiegspunkt einer Funktion enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt `TRUE` zurück, wenn der Block den Einstiegspunkt enthält. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Es ist möglich, dass ein Stapel Rahmen nicht der Anfang einer Funktion ist, da der Frame eine Inline Methode oder Funktion darstellt, die in eine Funktion eingefügt wurde.

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)