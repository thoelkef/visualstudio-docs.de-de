---
title: "prototype-Eigenschaft (WeakMap) | Microsoft Docs"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype-Eigenschaft (WeakMap)
Gibt einen Verweis auf den Prototyp für ein `WeakMap`\-Objekt zurück.  
  
## Syntax  
  
```javascript  
weakmap.prototype  
```  
  
## Hinweise  
 Das `weakmap`\-Argument ist der Name eines `WeakMap`\-Objekts.  
  
 Mit der `prototype`\-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `WeakMap`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements der `WeakMap` zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `WeakMap.prototype` hinzu, und verwenden Sie sie dann.  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]