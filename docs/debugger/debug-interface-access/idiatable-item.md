---
title: "IDiaTable::Item | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaTable::Item-Methode"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Verweis auf den angegebenen Eintrag in der Tabelle ab.  
  
## Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### Parameter  
 `index`  
 \[in\]  Der Index des Tabelleneintrags im Bereich von 0 bis \-1, wobei `count``count` von der [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)Methode zurückgegeben wird.  
  
 `element`  
 \[out\]  Gibt ein `IUnknown`\-Objekt zurück, das den angegebenen Tabelleneintrag darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Eine Tabelle enthält eine Auflistung von Objekten dar.  Je nach diesen Objekten kann der Parameter Element an die entsprechende Schnittstelle umgewandelt werden.  Wenn z. B. eine Tabelle [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)\-Objekte enthält, dann kann der Parameter Element der `IDiaSegment`\-Schnittstelle umgewandelt werden.  
  
 Es handelt sich um eine allgemeine Ansatz mehr, um die `QueryInterface`\-Methode in der [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Enumeratorschnittstelle für die entsprechende Schnittstelle aufzurufen und der spezifischen Methoden des Enumerators zu verwenden, um den Inhalt auf die Tabellen zuzugreifen.  Zeigen Sie die [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)\-Schnittstelle als Beispiel.  
  
## Siehe auch  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)