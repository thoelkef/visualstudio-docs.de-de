---
title: 'Idiatable:: Item | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 12d04da8ea2c2a136b61924578fcb925b17fc12f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 [in] Der Index des Eintrags Tabelle im Bereich von 0 bis `count`-1 und, in denen `count` wird zurückgegeben, indem Sie die [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)Methode.  
  
 `element`  
 [out] Gibt ein `IUnknown` Objekt, das dem angegebenen Verzeichniseintrag darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Eine Tabelle stellt eine Auflistung von Objekten dar. In Abhängigkeit von diesen Objekten kann der Elementparameter in der entsprechenden Schnittstelle umgewandelt werden. Wenn eine Tabelle enthält z. B. [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) Objekte aufweist, und klicken Sie dann in der Elementparameter umgewandelt werden kann die `IDiaSegment` Schnittstelle.  
  
 Es ist ein gängigerer Ansatz zum Aufrufen der `QueryInterface` Methode in der [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Benutzeroberfläche für die entsprechenden Enumerator-Schnittstelle und den Enumerator spezifischen Methoden Zugriff auf den Tabelleninhalt zu verwenden. Finden Sie unter der [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) Schnittstelle für ein Beispiel.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)