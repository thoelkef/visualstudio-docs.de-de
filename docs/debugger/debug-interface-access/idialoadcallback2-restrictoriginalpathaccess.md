---
title: 'IDiaLoadCallback2:: RestrictOriginalPathAccess | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bcdaa7c1896a0ef29706e3650ad8ac56537f778
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742996"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Bestimmt, ob es in Ordnung ist, im ursprünglichen Debugverzeichnis nach einer PDB-Datei zu suchen.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jeder andere Rückgabecode als `S_OK` verhindert das Suchen nach einer PDB-Datei im ursprünglichen Debugverzeichnis. Das ursprüngliche Debugverzeichnis ist der Pfad zu der Symbol Datei, die in die ausführbare Datei kompiliert wird, wenn Debugging aktiviert ist. Dieser Pfad ist nicht notwendigerweise identisch mit dem Pfad, in dem die ausführbare Datei vorhanden ist.

## <a name="see-also"></a>Siehe auch
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)