---
title: "length-Eigenschaft (String) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Zeichenfolgen [Visual Studio], Länge"
  - "Length-Eigenschaft"
  - "length-Eigenschaft (String)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# length-Eigenschaft (String) (JavaScript)
Gibt die Länge eines `String`\-Objekts zurück.  
  
> [!WARNING]
>  JavaScript\-Zeichenfolgen sind unveränderlich, sodass die Länge einer Zeichenfolge nicht geändert werden.  
  
## Syntax  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## Hinweise  
 Die `length`\-Eigenschaft enthält eine ganze Zahl, welche die Anzahl von Zeichen im `String`\-Objekt angibt.  Das letzte Zeichen im `String`\-Objekt hat den Index i`length` – 1.  
  
## Beispiel  
 Im folgenden Code wird die Verwendung von `length` veranschaulicht.  JavaScript\-Zeichenfolgen sind unveränderlich und können nicht direkt geändert werden.  Sie können jedoch die umgekehrte Zeichenfolge in ein Array schreiben und dann `join` mit dem leeren Zeichen aufrufen, wodurch eine Zeichenfolge ohne Trennzeichen erstellt wird.  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]