---
title: 'Idiaframedata:: Get_functionparent | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20f9dac750f9ff9723e4f3669f9e9a124d728a9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830343"
---
# <a name="idiaframedatagetfunctionparent"></a>IDiaFrameData::get_functionParent
Ruft eine Schnittstelle für den Rahmen für die einschließende Funktion ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_functionParent ( 
   IDiaFrameData** pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt eine [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt für die einschließende Funktion.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)