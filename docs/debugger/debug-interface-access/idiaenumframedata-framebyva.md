---
title: IDiaEnumFrameData::frameByVA | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9889a4f4add318209728bb09ac5c469c1fa836fe
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744651"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Gibt einen Frame nach der virtuellen Adresse (VA) zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parameter
 virtualAddress

in VA des interessanten Frames.

 Rahmen

vorgenommen Gibt ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt zurück, das den Frame darstellt, der die angegebene Adresse enthält.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine Frame Daten mit der angegebenen Adresse übereinstimmen. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)