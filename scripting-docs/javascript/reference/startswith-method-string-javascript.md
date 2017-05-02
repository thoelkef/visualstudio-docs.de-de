---
title: "startsWith-Methode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# startsWith-Methode (String) (JavaScript)
Gibt einen Wert zurück, der angibt, ob eine Zeichenfolge oder Teilzeichenfolge mit einer anderen angegebenen Zeichenfolge beginnt.  
  
## Syntax  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### Parameter  
 `stringObj`  
 Erforderlich.  Das string\-Objekt, nach dem gesucht werden soll.  
  
 `str`  
 Erforderlich.  Die Suchzeichenfolge.  
  
 `position`  
 Optional.  Die Position des ersten Zeichens für die Suche im string\-Objekt, beginnend mit 0.  
  
## Rückgabewert  
 Wenn die bei `position` beginnende Zeichenfolge mit der Suchzeichenfolge beginnt, gibt die `startsWith`\-Methode `true` zurück; andernfalls gibt sie `false` zurück.  
  
## Ausnahmen  
 Wenn `str` ein `RegExp` ist, wird ein `TypeError` ausgelöst.  
  
## Hinweise  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]