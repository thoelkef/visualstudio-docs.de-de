---
title: 'Idiainjetedsource:: get_sourceCompression | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9428b30df82d92a8c74511644aaf97f2166807a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743322"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Ruft den Indikator der verwendeten Quell Komprimierung ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Indikator der verwendeten Quell Komprimierung zurück. Der Wert 0 (null) gibt an, dass keine Quell Komprimierung verwendet wurde.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der von dieser Methode zurückgegebene Wert ist spezifisch für den verwendeten Compiler. Ein Compiler kann z. b. die Codierung der Lauf Zeit Länge oder der im Huffman-Stil verwendeten Komprimierung verwenden.

## <a name="see-also"></a>Siehe auch
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)