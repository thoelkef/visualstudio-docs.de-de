---
title: "parseInt-Funktion (JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt-Methode"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# parseInt-Funktion (JavaScript)
Konvertiert eine Zeichenfolge in eine ganze Zahl.  
  
## Syntax  
  
```  
parseInt(numString, [radix])   
```  
  
## Parameter  
 `numString`  
 Erforderlich.  Eine Zeichenfolge, die in eine Zahl konvertiert werden soll.  
  
 `radix`  
 Optional.  Eine Zahl zwischen 2 und 36, welche die Basis der Zahl in `numString` angibt.  Wenn dieses Argument nicht angegeben wird, gelten Zeichenfolgen mit dem Präfix "0x" als hexadezimale Zahl.  Alle anderen Zeichenfolgen werden als dezimale Zahl betrachtet.  
  
## Hinweise  
 Die `parseInt`\-Funktion gibt einen ganzzahligen Wert gleich der Zahl zurück, die in `numString` enthalten ist.  Falls kein Präfix von `numString` erfolgreich in eine ganze Zahl umgewandelt werden kann, wird `NaN` \(Not a Number\) zurückgegeben.  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Eine Überprüfung auf `NaN` können Sie mit der `isNaN`\-Funktion durchführen.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  Ab [!INCLUDE[jsv9textspecific](../../includes/jsv9textspecific-md.md)] behandelt die `parseInt`\-Funktion eine Zeichenfolge mit dem Präfix "0" nicht als oktale Zahl.  Wenn Sie die `parseInt`\-Funktion jedoch nicht verwenden, können Zeichenfolgen mit dem Präfix "0" weiterhin als oktale Zahlen interpretiert werden.  Weitere Informationen über ganze oktale Zahlen finden Sie unter [Datentypen](../../javascript/data-types-javascript.md).  
  
## Siehe auch  
 [isNaN\-Funktion](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat\-Funktion](../../javascript/reference/parsefloat-function-javascript.md)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)   
 [valueOf\-Methode \(Objekt\)](../../javascript/reference/valueof-method-object-javascript.md)