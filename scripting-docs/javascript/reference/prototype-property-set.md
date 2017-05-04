---
title: "prototype-Eigenschaft (Set) | Microsoft Docs"
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
ms.assetid: a075d5a6-e502-4636-85fc-1af001b8ac35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype-Eigenschaft (Set)
Gibt einen Verweis auf den Prototyp für einen Satz zurück.  
  
## Syntax  
  
```javascript  
set.prototype  
```  
  
## Hinweise  
 Das `set`\-Argument ist der Name eines Satzes.  
  
 Mit der `prototype`\-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Set`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Satzes zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Set.prototype` hinzu, und verwenden Sie sie dann.  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]