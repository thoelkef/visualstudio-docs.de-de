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
ms.openlocfilehash: cd6f5219edf9426067a4431936caa2186604e1cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741539"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Ruft einen Stapel Rahmen Enumerator für x86-Plattformen ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `pHelper`

in Das [hilfsidiastackwalkhelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) -Objekt.

 `ppEnum`

vorgenommen Gibt ein [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) -Objekt zurück, das eine Liste von [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) -Objekten enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Um eine Stapel Rahmen Liste auf einer beliebigen anderen Plattform abzurufen, nennen Sie die [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) -Methode.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)