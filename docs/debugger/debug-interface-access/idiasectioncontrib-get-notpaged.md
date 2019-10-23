---
title: 'IDiaSectionContrib:: get_notPaged | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cae6940ce69bf9cd39c1002cc522af993fc59b6d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742587"
---
# <a name="idiasectioncontribget_notpaged"></a>IDiaSectionContrib::get_notPaged
Ruft ein Flag ab, das angibt, ob für den Abschnitt nicht genügend Arbeitsspeicher verfügbar ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_notPaged ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`
- [out, retval] Gibt `TRUE` zurück, wenn der Abschnitt nicht ausgelagert werden kann. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)