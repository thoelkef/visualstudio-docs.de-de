---
title: "for...in-Anweisung (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Iterationsanweisungen, for...in-Anweisung"
  - "Schleifenstruktur, for...in-Anweisungen"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# for...in-Anweisung (JavaScript)
Führt eine oder mehrere Anweisungen für jede Eigenschaft eines Objekts oder jedes Element eines Arrays aus.  
  
## Syntax  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## Parameter  
 `variable`  
 Erforderlich.  Eine Variable, die jeder Eigenschaftenname von `object` oder jeder Elementindex eines `array` sein kann.  
  
 `object`, `array`  
 Optional.  Ein Objekt oder Array, das durchlaufen werden soll.  
  
 `statements`  
 Optional.  Eine oder mehrere Anweisungen, die für jede Eigenschaft von `object` bzw. jedes Element von `array` ausgeführt werden sollen.  Hierbei kann es sich um eine Verbundanweisung handeln.  
  
## Hinweise  
 Zu Beginn jeder Schleifeniteration ist der Wert von `variable` der nächste Eigenschaftenname von `object` oder der nächste Elementindex von `array`.  Sie können `variable` dann in allen Anweisungen innerhalb der Schleife verwenden, um auf die Eigenschaft von `object` oder das Element von `array` zu verweisen.  
  
 Die Eigenschaften eines Objekts werden nicht auf bestimmte Art zugewiesen.  Sie können eine bestimmte Eigenschaft nicht mit ihrem Index, sondern nur mit dem Namen der Eigenschaft angeben.  
  
 Das Durchlaufen eines Arrays wird in Elementreihenfolge ausgeführt, also 0, 1, 2.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `for...in`\-Anweisung für ein Objekt, das als assoziatives Array verwendet wird.  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## Beispiel  
 Dieses Beispiel veranschaulicht die Verwendung der `for ... in`\-Anweisung zum Durchlaufen eines `Array`\-Objekts, das expando\-Eigenschaften aufweist.  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Verwenden Sie das `Enumerator`\-Objekt, um die Member einer Auflistung zu durchlaufen.  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Siehe auch  
 [for\-Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [while\-Anweisung](../../javascript/reference/while-statement-javascript.md)