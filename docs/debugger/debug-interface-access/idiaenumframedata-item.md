---
title: 'IDiaEnumFrameData:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c15f395e7f4aa576c5f69b0f1c61f37ca808fb6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744611"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Ruft ein Frame-Datenelement mithilfe eines Indexes ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Parameter
 Index

in Der Index des [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekts, das abgerufen werden soll. Der Index liegt im Bereich von 0 bis `count`-1, wobei `count` von der [IDiaEnumFrameData:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) -Methode zurückgegeben wird.

 section

vorgenommen Gibt ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt zurück, das das gewünschte Frame Datenelement darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)