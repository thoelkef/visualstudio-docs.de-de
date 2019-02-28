---
title: IDiaStackWalker::getEnumFrames | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9011f0becd893fa4ca966c40013844b0be47e46d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629390"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Ruft einen Stack-Frame-Enumerator für X86 Plattformen.

## <a name="syntax"></a>Syntax

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `pHelper`

[in] Das Hilfsprogramm [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) Objekt.

 `ppEnum`

[out] Gibt eine [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) -Objekt, das eine Liste der enthält [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) Objekte.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
 Um eine Liste der Stack-Frame auf eine andere Plattform zu erhalten, rufen die [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)