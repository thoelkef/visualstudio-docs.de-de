---
title: 'Idiastackwalkhelper:: Searchforreturnaddressstart | Microsoft-Dokumentation'
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
ms.openlocfilehash: a311b10f2fc5b53daff58e93feec3a9cd6077d14
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623345"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Sucht den angegebenen Stapelrahmen für eine Absenderadresse an oder in der Nähe der Adresse angegebenen Stapel an.

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

[in] Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) Objekt, das den aktuellen Stapelrahmen darstellt.

 `startAddress`

[in] Eine Adresse des virtuellen Arbeitsspeichers aus dem die Suche beginnen soll.

 `ReturnAddress`

[out] Gibt die nächste Funktion zurückgeben Adresse `startAddress`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)