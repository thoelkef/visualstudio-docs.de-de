---
title: "prototype-Eigenschaft (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype-Eigenschaft (Intl.DateTimeFormat)
Gibt einen Verweis auf den Prototyp für eine Formatierung zurück.  
  
## Syntax  
  
```javascript  
dateTimeFormat.prototype  
```  
  
## Hinweise  
 Das `dateTimeFormat`\-Argument ist der Name einer Formatierung.  
  
 Mit der `prototype`\-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Intl.DateTimeFormat`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Satzes zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Intl.DateTimeFormat.prototype` hinzu, und verwenden Sie sie dann.  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]