---
title: "slice-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "slice-Methode"
  - "Zeichenfolgen [Visual Studio], zurückgegebene Zeichen"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# slice-Methode (String) (JavaScript)
Gibt einen Abschnitt einer Zeichenfolge zurück.  
  
## Syntax  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## Parameter  
 `stringObj`  
 Erforderlich.  Ein `String`\-Objekt oder Zeichenfolgenliteral.  
  
 `start`  
 Erforderlich.  Der Index am Anfang des angegebenen Abschnitts von `stringObj`.  
  
 `end`  
 Dies ist optional.  Der Index am Ende des angegebenen Abschnitts von `stringObj`.  Die Teilzeichenfolge enthält die Zeichen bis zum, aber nicht einschließlich des von `end` angegebenen Zeichens.  Wenn dieser Wert nicht angegeben wird, erstreckt sich die Teilzeichenfolge bis zum Ende von `stringObj`.  
  
## Hinweise  
 Die `slice`\-Methode gibt ein `String`\-Objekt zurück, das den angegebenen Abschnitt von `stringObj` enthält.  
  
 Die `slice`\-Methode kopiert bis zu dem Zeichen, das durch `end` angegeben wird. Das Zeichen ist jedoch nicht in der Kopie enthalten.  
  
 Falls `start` negativ ist, wird es als *length* \+ `start` behandelt, wobei *length* der Länge der Zeichenfolge entspricht.  Wenn `end` negativ ist, wird dieser Parameter als *length* \+ `end` behandelt.  Wird `end` ausgelassen, wird das Kopieren bis zum Ende von `stringObj` fortgesetzt.  Falls `end` vor `start` auftritt, werden keine Elemente in die neue Zeichenfolge kopiert.  
  
## Beispiel  
 Im ersten Beispiel gibt die `slice`\-Methode die gesamte Zeichenfolge zurück.  Im zweiten Beispiel gibt die `slice`\-Methode die gesamte Zeichenfolge, mit Ausnahme des letzten Zeichens zurück.  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [slice\-Methode \(Array\)](../../javascript/reference/slice-method-array-javascript.md)