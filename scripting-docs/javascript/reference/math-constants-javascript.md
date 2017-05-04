---
title: "Math-Konstanten (JavaScript) | Microsoft Docs"
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
  - "LN2-Konstante [JavaScript]"
  - "E-Konstante [JavaScript]"
  - "LOG10E-Konstante [JavaScript]"
  - "SQRT1_2-Konstante [JavaScript]"
  - "LOG2E-Konstante [JavaScript]"
  - "Math.SQRT2-Konstante [JavaScript]"
  - "PI-Konstante [JavaScript]"
  - "Math.LOG2E-Konstante [JavaScript]"
  - "Konstanten [JavaScript], Math"
  - "Math.E-Konstante [JavaScript]"
  - "Logarithmuskonstante [JavaScript]"
  - "Math.LOG10E-Konstante [JavaScript]"
  - "Math.SQRT1_2-Konstante [JavaScript]"
  - "SQRT2-Konstante [JavaScript]"
  - "Quadratwurzelkonstante [JavaScript]"
  - "Math.PI-Konstante [JavaScript]"
  - "Math-Konstanten [JavaScript]"
  - "LN10-Konstante [JavaScript]"
  - "Math.LN2-Konstante [JavaScript]"
  - "Math.LN10-Konstante [JavaScript]"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math-Konstanten (JavaScript)
Mathematische Konstanten geben konstante Werte zurück, die Eigenschaften des `Math`\-Objekts sind.  
  
## Konstanten des Math\-Objekts  
 In der folgenden Tabelle sind konstante Werte aufgelistet, bei denen es sich um Eigenschaften des [Math\-Objekts](../../javascript/reference/math-object-javascript.md) handelt.  
  
|Konstante|Beschreibung|Ungefährer Wert|  
|---------------|------------------|---------------------|  
|`Math.E`|Die mathematische Konstante e.  Die Eulersche Zahl, Basis natürlicher Logarithmen.|2.718|  
|`Math.LN2`|Der natürliche Logarithmus von 2.|0.693|  
|`Math.LN10`|Der natürliche Logarithmus von 10.|2.302|  
|`Math.LOG2E`|Der Logarithmus zur Basis 2 von e.|1.443|  
|`Math.LOG10E`|Der Logarithmus zur Basis 10 von e.|0.434|  
|`Math.PI`|Pi.  Gibt das Verhältnis eines Kreisumfangs zum Kreisdurchmesser an.|3.14159|  
|`Math.SQRT1_2`|Die Quadratwurzel von 0,5 oder 1 geteilt durch die Quadratwurzel von 2.|0.707|  
|`Math.SQRT2`|Die Quadratwurzel von 2.|1.414|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `Math.PI`\-Konstante veranschaulicht.  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Math\-Objekt](../../javascript/reference/math-object-javascript.md)  
  
## Siehe auch  
 [Nummerkonstanten](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript\-Konstanten](../../javascript/reference/javascript-constants.md)