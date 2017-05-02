---
title: "prototype-Eigenschaft (WeakSet) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype-Eigenschaft (WeakSet)
Gibt einen Verweis auf den Prototyp für `WeakSet` zurück.  
  
## Syntax  
  
```javascript  
weakset.prototype  
```  
  
## Hinweise  
 Das `weakset`\-Argument ist der Name eines Satzes.  
  
 Mit der `prototype`\-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `WeakSet`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Satzes zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `WeakSet.prototype` hinzu, und verwenden Sie sie dann.  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]