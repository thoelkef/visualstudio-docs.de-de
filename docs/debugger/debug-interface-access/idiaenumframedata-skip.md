---
title: 'Idiaenumframedata:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d747149e18f831b9f57249503a64c37141c4daa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598478"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Überspringt eine angegebene Anzahl von Frames von Datenelementen in einer Enumerationsfolge.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 celt

[in] Die Anzahl der Frames-Datenelemente in der Enumerationsfolge übersprungen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` es sind keine weitere Datensätze zu überspringen.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)