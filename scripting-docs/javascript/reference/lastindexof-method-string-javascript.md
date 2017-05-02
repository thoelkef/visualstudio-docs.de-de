---
title: "lastIndexOf-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndexOf-Methode, String"
  - "String, lastIndexOf-Methode"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# lastIndexOf-Methode (String) (JavaScript)
Gibt die letzte Position einer Teilzeichenfolge in der Zeichenfolge zurück.  
  
## Syntax  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## Parameter  
 `strObj`  
 Erforderlich.  Ein `String`\-Objekt oder Zeichenfolgenliteral.  
  
 `substring`  
 Erforderlich.  Die zu suchende Teilzeichenfolge.  
  
 `startindex`  
 Optional.  Der Index, ab dem mit der Suche begonnen werden soll.  Wenn die Angabe fehlt, beginnt die Suche am Ende der Zeichenfolge.  
  
## Hinweise  
 Die **lastIndexOf**\-Methode gibt einen ganzzahligen Wert zurück, der den Beginn der untergeordneten Zeichenfolge innerhalb des `String`\-Objekts angibt.  Wird die untergeordnete Zeichenfolge nicht gefunden, ist der Rückgabewert \-1.  
  
 Wenn `startindex` negativ ist, wird für `startindex` der Wert 0 \(null\) verwendet.  Ist er größer als der größte Zeichenpositionsindex, wird er wie der größtmögliche Index behandelt.  
  
 Der Suchvorgang beginnt mit beim letzten Zeichen der Zeichenfolge.  Ansonsten ist diese Methode mit **indexOf** identisch.  
  
 Das folgende Beispiel veranschaulicht die Verwendung der **lastIndexOf**\-Methode.  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [indexOf\-Methode \(String\)](../../javascript/reference/indexof-method-string-javascript.md)