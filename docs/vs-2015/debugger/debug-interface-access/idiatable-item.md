---
title: 'Idisierbar:: Item | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574800"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft einen Verweis auf den angegebenen Eintrag in der Tabelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `index`  
 in Der Index des Tabellen Eintrags im Bereich von 0 bis `count` -1, wobei `count` von der [iditable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)-Methode zurückgegeben wird.  
  
 `element`  
 vorgenommen Gibt ein `IUnknown` Objekt zurück, das den angegebenen Tabelleneintrag darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Tabelle stellt eine Auflistung von-Objekten dar. Abhängig von diesen Objekten kann der Element Parameter in die entsprechende Schnittstelle umgewandelt werden. Wenn eine Tabelle z. b. [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) -Objekte enthält, kann der Element Parameter in die- `IDiaSegment` Schnittstelle umgewandelt werden.  
  
 Es ist ein häufiger Ansatz, die `QueryInterface` -Methode in der [idisierbaren](../../debugger/debug-interface-access/idiatable.md) -Schnittstelle für die entsprechende Enumeratorschnittstelle aufzurufen und mithilfe der spezifischen Methoden des Enumerators auf den Tabelleninhalt zuzugreifen. Ein Beispiel finden Sie in der [idiaenuminjetedsources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) -Schnittstelle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idisierbar:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
