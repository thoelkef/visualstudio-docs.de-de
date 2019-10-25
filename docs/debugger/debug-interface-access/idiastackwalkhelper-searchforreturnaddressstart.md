---
title: 'IDiaStackWalkHelper:: searchForReturnAddressStart | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0753cfe2d9ef8b08606185a5f57a3951f54e7de
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741336"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Durchsucht den angegebenen Stapel Rahmen nach einer Rückgabeadresse an oder in der Nähe der angegebenen Stapel Adresse.

## <a name="syntax"></a>Syntax

```C++
HRESULT searchForReturnAddressStart( 
   IDiaFrameData*  frame,
   ULONGLONG       startAddress,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Parameter
 `frame`

in Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt, das den aktuellen Stapel Rahmen darstellt.

 `startAddress`

in Eine Adresse für den virtuellen Speicher, von der aus gesucht werden soll.

 `ReturnAddress`

vorgenommen Gibt die nächstgelegene Funktions Rückgabeadresse für `startAddress` zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)