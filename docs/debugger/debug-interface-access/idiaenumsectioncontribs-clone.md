---
title: 'Idiaenumsectioncontrisb:: Clone | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Clone method
ms.assetid: 81d3f3a7-3684-4e5c-b028-29b268684a2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad6a561308999092344fe4c20038ec2cb78a86f4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744323"
---
# <a name="idiaenumsectioncontribsclone"></a>IDiaEnumSectionContribs::Clone
Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT Clone( 
   IDiaEnumSectionContrib** ppenum
);
```

#### <a name="parameters"></a>Parameter
 ppenum

vorgenommen Gibt ein [idiaenumsectioncontrisb](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) -Objekt zurück, das ein Duplikat des Enumerators enthält. Die Abschnitts Beiträge werden nicht dupliziert, sondern nur der Enumerator.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)