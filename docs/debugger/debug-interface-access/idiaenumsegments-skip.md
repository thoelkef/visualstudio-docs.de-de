---
title: 'IDiaEnumSegments:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efedd0e24c96259f1c9e9b6fc7522ee250bd4b25
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744170"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Überspringt eine angegebene Anzahl von Segmenten in einer enumerationssequenz.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der zu über springenden Segmente in der enumerationssequenz.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` zurückgegeben, wenn keine weiteren Segmente zum Überspringen vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)