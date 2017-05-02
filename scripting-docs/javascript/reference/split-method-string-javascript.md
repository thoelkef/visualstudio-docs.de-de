---
title: "split-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split-Methode"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# split-Methode (String) (JavaScript)
Teilt mithilfe des angegebenen Trennzeichens eine Zeichenfolge in untergeordnete Zeichenfolgen und gibt sie als Array zurück.  
  
## Syntax  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## Parameter  
 `stringObj`  
 Erforderlich.  Das aufzuteilende `String`\-Objekt oder \-Zeichenfolgenliteral.  Dieses Objekt wird nicht von der **split**\-Methode geändert.  
  
 `separator`  
 Optional.  Eine Zeichenfolge oder ein **Regular Expression**\-Objekt zum Identifizieren eines oder mehrerer Trennzeichen, die zur Unterteilung der Zeichenfolge verwendet werden.  Wenn das Trennzeichen ausgelassen wird, wird ein Array mit einem Element zurückgegeben, das die vollständige Zeichenfolge enthält.  
  
 `limit`  
 Optional.  Ein Wert, der zur Begrenzung der Anzahl von Elementen verwendet wird, die im Array zurückgegeben werden.  
  
## Rückgabewert  
 Das Ergebnis der **split**\-Methode ist ein Array von Zeichenfolgen. Diese ergeben sich durch die Unterteilung des `separator`\-Objekts an den Stellen, an denen `stringObj` auftritt.  Das `separator`\-Argument wird nicht als Bestandteil eines Arrayelements zurückgegeben.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **split**\-Methode.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [concat\-Methode \(String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Beispiel\-App für Bildlauf, Schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)