---
title: "constructor-Eigenschaft (Boolesch) | Microsoft Docs"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor-Eigenschaft (Boolesch)
Gibt die Funktion an, mit der ein Boolean\-Objekt erstellt wird.  
  
## Syntax  
  
```  
  
boolean.constructor([[value])  
```  
  
#### Parameter  
 `boolean`  
 Der Name des Boolean\-Objekts.  
  
 `value`  
 Optional.  Gibt den Wert des Boolean\-Objekts an.  Hierbei kann es sich um die Zahlen 1 oder 0 oder die Zeichenfolgen "true" oder "false" handeln.  
  
## Hinweise  
 Die `constructor`\-Eigenschaft enthält einen Verweis auf die Funktion, die Instanzen des Boolean\-Objekts erstellt.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der constructor\-Eigenschaft.  
  
```javascript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]