---
title: 'IDiaLoadCallback2:: RestrictReferencePathAccess | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3406052f4d5466b5b7f52a1da3490d35bbb0508f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742983"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Bestimmt, ob die Suche nach einer PDB-Datei in dem Pfad zulässig ist, in dem sich die exe-Datei befindet.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein anderer Rückgabecode als `S_OK`, um zu verhindern, dass eine PDB-Datei im Pfad vorhanden ist, in dem sich die exe-Datei befindet.

## <a name="see-also"></a>Siehe auch
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)