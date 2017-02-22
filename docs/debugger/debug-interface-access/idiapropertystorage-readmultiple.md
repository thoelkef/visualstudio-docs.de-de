---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Reads aktuellen Eigenschaften des angegebenen Eigenschaft an.  
  
## Syntax  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### Parameter  
 `cpspec`  
 \[in\]  Anzahl von Eigenschaften im angegebenen `rgpspec` Array.  Wenn Null, die Methode zurückgibt, gibt aber keine Eigenschaften als `S_OK` Erfolgs Code zurück.  
  
 `rgpspec`  
 \[in\]  Ein Array von zu lesenden Eigenschaften.  Eigenschaften können entweder von einer Eigenschaften\-ID oder durch einen optionalen Zeichenfolgennamen angegeben werden.  Es ist nicht erforderlich, Eigenschaften in einer bestimmten Reihenfolge im Array an.  Das Array kann doppelte Eigenschaften mit dem Ergebnis der doppelten Eigenschaftswerte bei Rückgabe für einfache Eigenschaften enthalten.  Nicht\-SIMPLE\-Eigenschaften sollten den Zugriff zurückgeben, der auf einem Versuch, ein zweites Mal öffnen, verweigert wird.  Das Array kann eine Kombination aus Eigenschaften\-ID und IDs Zeichenfolge enthalten.  Dieses Array muss mindestens `cpspec` Zahl Eigenschaftswerte verfügen.  
  
 `rgvar`  
 \[in, out\]  Ein Array mit Werten für jede Eigenschaft ausgefüllt wird, oder legt `PROPVARIANT` Strukturen \(im Microsoft.VisualStudio.OLE.Interop\-Namespace\).  Das Array muss mindestens `cpspec`\-Elemente an.  Der Aufrufer muss nicht die Werte im Array zu initialisieren.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn eine oder mehrere der Eigenschaften nicht gefunden wurden.  Gibt andernfalls ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Wenn eine Eigenschaft nicht gefunden wurde, enthält die entsprechenden Eintrag im `rgvar` Array `VARIANT` mit dem Typ von `VT_EMPTY`.  
  
## Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)