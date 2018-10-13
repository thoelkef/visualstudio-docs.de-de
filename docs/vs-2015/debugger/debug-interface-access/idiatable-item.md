---
title: 'Idiatable:: Item | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30b2de7590a20c3d0b9e1ec911779d407a46b1f6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289119"
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
 [in] Der Index des Eintrags Tabelle im Bereich von 0 bis `count`-1 und, in dem `count` wird zurückgegeben, durch die [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)Methode.  
  
 `element`  
 [out] Gibt eine `IUnknown` Objekt, das den angegebenen Eintrag darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Eine Tabelle stellt eine Auflistung von Objekten dar. Abhängig von diesen Objekten kann der Elementparameter in die entsprechende Schnittstelle umgewandelt werden. Wenn eine Tabelle enthält z. B. [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) Objekte aufweist, und klicken Sie dann der Elementparameter in umgewandelt werden kann die `IDiaSegment` Schnittstelle.  
  
 Dies ist ein häufiger Ansatz zum Aufrufen der `QueryInterface` -Methode in der die [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Schnittstelle für die entsprechenden Enumerator-Schnittstelle, und spezifische Methoden der Enumerator auf den Inhalt der Tabelle zugreifen. Finden Sie unter den [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) Schnittstelle für ein Beispiel.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



