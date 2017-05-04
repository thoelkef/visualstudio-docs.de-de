---
title: "Math.abs-Funktion (JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Absolute Werte, berechnen"
  - "Absolute Werte"
  - "Numerische Ausdrücke"
  - "abs-Methode"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Math.abs-Funktion (JavaScript)
Gibt den absoluten Wert einer Zahl zurück \(der Wert dieser Zahl ohne positivem oder negativem Vorzeichen\).  Beispielsweise sind der absolute Wert von \-5 und der absolute Wert von 5 gleich.  
  
## Syntax  
  
```  
Math.abs(number)  
```  
  
#### Parameter  
 Das erforderliche `number`\-Argument ist ein numerischer Ausdruck, für den der absolute Wert benötigt wird.  
  
## Rückgabewert  
 Der absolute Wert des `number`\-Arguments.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `abs`\-Funktion.  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Math\-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## Siehe auch  
 [Math\-Objekt](../../javascript/reference/math-object-javascript.md)