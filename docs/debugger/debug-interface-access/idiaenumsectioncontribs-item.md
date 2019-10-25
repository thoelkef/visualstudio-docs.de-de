---
title: 'Idiaenumsectioncontrisb:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021b5016bd0e0039f2bf175102dc44f04dabaab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744297"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Ruft Abschnitts Beiträge mithilfe eines Indexes ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>Parameter
 Index

in Der Index des abzurufenden [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) -Objekts. Der Index liegt im Bereich von 0 bis `count`-1, wobei `count` von der [idiaenumsectioncontrisb:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) -Methode zurückgegeben wird.

 section

vorgenommen Gibt ein [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) -Objekt zurück, das den gewünschten Abschnitts Beitrag darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)