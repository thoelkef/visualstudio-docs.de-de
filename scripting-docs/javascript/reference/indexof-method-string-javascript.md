---
title: "indexOf-Methode (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "indexOf-Methode, Zeichenfolge"
  - "Zeichenfolge, indexOf-Methode"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# indexOf-Methode (String) (JavaScript)
Gibt die Position des ersten Vorkommens einer Teilzeichenfolge zurück.  
  
## Syntax  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## Parameter  
 `strObj`  
 Erforderlich.  Ein `String`\-Objekt oder \-Zeichenfolgenliteral.  
  
 `subString`  
 Erforderlich.  Die in der Zeichenfolge zu suchende Teilzeichenfolge  
  
 `startIndex`  
 Dies ist optional.  Der Index, an dem mit der Suche im `String`\-Objekt begonnen werden soll.  Ohne diese Angabe wird am Beginn der Zeichenfolge mit der Suche begonnen.  
  
## Hinweise  
 Die **indexOf**\-Methode gibt den Anfang der Teilzeichenfolge im `String`\-Objekt zurück.  Wird die Teilzeichenfolge nicht gefunden, ist der Rückgabewert – 1.  
  
 Wenn `startindex` negativ ist, wird für `startindex` der Wert 0 \(null\) verwendet.  Wenn sie größer als der höchste Index ist, wird sie als der höchste Index behandelt.  
  
 Die Suche erfolgt von links nach rechts.  Ansonsten ist diese Methode mit **lastindexOf** identisch.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **indexOf**\-Methode.  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [lastIndexOf\-Methode \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Beispiel\-App für Bildlauf, Schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)