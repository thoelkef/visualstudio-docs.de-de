---
title: 'Idisierbar:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738717"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Ruft einen Verweis auf den angegebenen Eintrag in der Tabelle ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>Parameter
 `index`

in Der Index des Tabellen Eintrags im Bereich von 0 bis `count`-1, in dem `count` von der [iditable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)-Methode zurückgegeben wird.

 `element`

vorgenommen Gibt ein `IUnknown` Objekt zurück, das den angegebenen Tabelleneintrag darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Eine Tabelle stellt eine Auflistung von-Objekten dar. Abhängig von diesen Objekten kann der Element Parameter in die entsprechende Schnittstelle umgewandelt werden. Wenn eine Tabelle z. b. [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) -Objekte enthält, kann der Element Parameter in die `IDiaSegment`-Schnittstelle umgewandelt werden.

 Es ist ein häufiger Ansatz, die `QueryInterface`-Methode in der [idisierbaren](../../debugger/debug-interface-access/idiatable.md) Schnittstelle für die entsprechende Enumeratorschnittstelle aufzurufen und mithilfe der spezifischen Methoden des Enumerators auf den Tabelleninhalt zuzugreifen. Ein Beispiel finden Sie in der [idiaenuminjetedsources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) -Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)