---
title: 'IDiaEnumStackFrames:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffde40e221823d9656c4b6414b14067ac9d0537a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744043"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Ruft eine angegebene Anzahl von Stapel Rahmenelementen aus der enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der StackFrame-Elemente im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Ein Array, das mit den angeforderten [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) -Objekten aufgefüllt werden soll.

 pceltFetched

vorgenommen Gibt die Anzahl der Stapel Rahmenelemente im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine Stapel Rahmen mehr vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)