---
title: 'IDiaEnumFrameData:: Skip | Microsoft-Dokumentation'
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
ms.openlocfilehash: c49aaf1f648a52e1701088b6579eda55cde6c355
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744569"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Überspringt eine angegebene Anzahl von Frame-Datenelementen in einer enumerationssequenz.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der zu über springenden Frame-Datenelemente in der enumerationssequenz.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` zurückgegeben, wenn keine weiteren zu über springenden Datensätze vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)