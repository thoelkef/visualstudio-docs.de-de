---
title: IDiaStackWalker::getEnumFrames2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6de78b5553719def2fd7ef9c6adb55e823aac34
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741532"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Ruft einen Stapel Rahmen Enumerator für einen bestimmten Plattformtyp ab.

## <a name="syntax"></a>Syntax

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `cpuid`

in Ein Wert aus der [CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) -enumerationsenumeration, der den Plattformtyp angibt.

 `pHelper`

in Das [hilfsidiastackwalkhelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) -Objekt.

 `ppEnum`

vorgenommen Gibt ein [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) -Objekt zurück, das eine Liste von [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) -Objekten enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Rufen Sie zum Abrufen einer Stapel Rahmen Liste nur für die x86-Plattform die [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) -Methode auf.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [CV_CPU_TYPE_e-Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)