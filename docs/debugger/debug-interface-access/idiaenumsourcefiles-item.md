---
title: 'IDiaEnumSourceFiles:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 352c9516180c0ee0021fca4e0913f154f3b8d46f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744096"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Ruft eine Quelldatei mithilfe eines Indexes ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Parameter
 Index

in Der Index des [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekts, das abgerufen werden soll. Der Index liegt im Bereich von 0 bis `count`-1, wobei `count` von der [IDiaEnumSourceFiles:: get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) -Methode zurückgegeben wird.

 sourceFile

vorgenommen Gibt ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekt zurück, das die gewünschte Quelldatei darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)