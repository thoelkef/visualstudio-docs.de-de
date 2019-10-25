---
title: 'IDiaFrameData:: get_allocatesBasePointer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 283ef71b32c186956804cb3afe121af53a99abfc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743651"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Ruft ein Flag ab, das angibt, ob der Basis Zeiger für Code in diesem Adressbereich zugeordnet wird. Diese Methode ist veraltet.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt `TRUE` zurück, wenn ein Basis Zeiger zugeordnet ist. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Eigenschaft sollte nur von Code verwendet werden, auf den zuvor FPO_DATA zugegriffen wurde, oder wenn die von der [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) -Methode zurückgegebene Programm Zeichenfolge `NULL` ist. Andernfalls enthält die Programm Zeichenfolge alle Informationen, die erforderlich sind, um vorherige Registerwerte zu berechnen.

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)